<template>
  <table class="table" ref="slotContainer">
    <slot />
  </table>
</template>

<script>
export default {
  name: "Status",
  props: ["value"],
  mounted() {
    if (process.env.NODE_ENV !== "development") {
      this.$nextTick().then(this.fixSlot.bind(this));
    }
  },
  methods: {
    fixSlot() {
      this.$refs.slotContainer.innerHTML = "";
      this.$refs.slotContainer.append(document.createElement("slot"));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
