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
      <tbody v-if="rowStates">
        <tr
          v-for="( row, index ) in rowStates"
          :key="index"
          v-bind:class="{
          editinRow: row.checked
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
                :key="row.checked"
                type="checkbox"
                :checked="row.checked"
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
                <Status v-if="!row.checked" :value="row[ prop ]" />
                <select v-model="row[prop]" v-else>
                  <option value="alta">Alta</option>
                  <option value="confirmado">Confirmado</option>
                  <option value="sospecha">Sospecha</option>
                  <option value="descartado">Descartado</option>
                </select>
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
import Status from "./Status";

export default {
  name: "Table",
  components: {
    Typography,
    Buttom,
    Status
  },
  data() {
    return {
      rowStates: []
    };
  },
  props: {
    columns: { type: Object, required: true },
    rows: { type: Array, required: true },
    allClick: { type: Function, default: () => null },
    clickOne: { type: Function, default: () => null }
  },
  mounted: function() {
    console.log("entrando en el mounted");

    if (this.rows) {
      console.log("entrando en el mounted [[rows]]", this.rows);
      this.rowStates = this.rows.map(row => {
        return {
          ...row,
          checked: row.checkbox
        };
      });
    }
  },
  methods: {
    clickOnePrivate(position, value) {
      this.rowStates = this.rowStates.map((row, index) => {
        return {
          ...row,
          checked: index === position ? value : row.checked
        };
      });
    },
    clickAllPrivate(value) {
      this.rowStates = this.rowStates.map(row => {
        return {
          ...row,
          checked: value
        };
      });
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

