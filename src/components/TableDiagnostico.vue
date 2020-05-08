<template>
  <div class="table-responsive">
    <table class="table">
      <thead>
        <tr v-if="columns">
          <th
            v-for="( column, prop ) in columns"
            :key="prop"
            v-bind:class="{
            textCenter: prop==='checkbox'
          }"
          >
            <input
              :key="column"
              v-if="prop === 'checkbox'"
              :checked="column"
              type="checkbox"
              @click="(e)=>{
              clickAllPrivate(e.target.checked);
              }"
            />
            {{ prop !== 'checkbox' ? column : '' }}
          </th>
        </tr>
      </thead>
      <tbody v-if="rows">
        <tr
          v-for="( row, index ) in rows"
          :key="index"
          v-bind:class="{
          editinRow: checks.indexOf(index)!==-1
        }"
        >
          <td
            v-for="( _, prop ) in columns"
            :key="prop"
            v-bind:class="{
            textCenter: prop==='checkbox'
          }"
          >
            <slot :row="row" :prop="prop">
              <input
                v-if="prop==='checkbox'"
                :key="checks.indexOf(index)!==-1"
                type="checkbox"
                :checked="checks.indexOf(index)!==-1"
                @click="(e)=>{
                  clickOnePrivate(index, e.target.checked);
                }"
              />
              <Typography
                v-else-if="(typeof row[prop]==='string') && prop!=='estado'"
                :weight="row[ prop ].weight"
                :size="row[ prop ].size"
                :type="row[ prop ].type"
                :variant="row[ prop ].variant"
              >{{row[ prop ]}}</Typography>
              <div v-else-if="prop==='acciones'">
                <Buttom
                  v-for="button in row[ prop ]"
                  @onClick="button.onClick()"
                  :key="button.text"
                  :variant="button.variant"
                  :icon="button.icon"
                  :color="button.color"
                >{{button.text}}</Buttom>
              </div>
              <div v-else-if="prop==='estado'">
                <HandleState
                  :index="index"
                  :editing="checks.indexOf(index)!==-1"
                  :currentValue="row[ prop ]"
                />
              </div>
              <Typography
                v-else
                :weight="row[ prop ].weight"
                :size="row[ prop ].size"
                :type="row[ prop ].type"
                :variant="row[ prop ].variant"
              >{{row[ prop ].text}}</Typography>
            </slot>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Typography from "./Typography";
import Buttom from "./Button.vue";
import HandleState from "./HandleState";

export default {
  name: "Table",
  components: {
    Typography,
    Buttom,
    HandleState
  },
  data() {
    return {
      checks: [],
      statusChanged: {}
    };
  },
  props: {
    columns: { type: Object, required: true },
    rows: { type: Array, required: true },
    allClick: { type: Function, default: () => null },
    clickOne: { type: Function, default: () => null }
  },
  methods: {
    clickOnePrivate(position, value) {
      if (value && this.checks.indexOf(position) === -1) {
        this.checks.push(position);
      } else {
        this.checks = this.checks.filter(val => val !== position);
      }
    },
    clickAllPrivate(value) {
      this.checks = [];
      if (value) {
        this.checks = this.rows.map((el, index) => index);
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.editinRow {
  background-color: #b8eae3;
}
.table-responsive {
  width: 100%;
  overflow: auto;
}
.table {
  border-collapse: collapse;
  width: 100%;
  font-family: Helvetica, Arial, sans-serif;
}
.table tr {
  border-bottom: 1px solid #e8e8e8;
}
.table tr th {
  padding: 16px 8px 18px;
}
.table tr td {
  padding: 8px;
}

.textCenter {
  text-align: center;
}

.table thead {
  background-color: #fafafa;
}
</style>

