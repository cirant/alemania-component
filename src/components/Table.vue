<template>
  <div class="table-responsive">
    <table class="table">
      <thead>
        <tr>
          <th v-for="( column, prop ) in columns" :key="prop">{{ column }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="( row, index ) in rows" :key="index">
          <td v-for="( _, prop ) in columns" :key="prop">
            <slot :row="row" :prop="prop">{{ row[ prop ] }}</slot>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "Table",
  props: {
    columns: { type: Object, required: true },
    rows: { type: Array, required: true }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
.table thead {
  background-color: #fafafa;
}
</style>
