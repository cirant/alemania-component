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
    this.$nextTick().then(this.fixSlot.bind(this));
  },
  methods: {
    // This is where the magic happens
    fixSlot() {
      // // remove all the innerHTML that vue has place where the slot should be
      // // // replace it with a new slot, if you are using named slot you can just add attributes to the slot
      this.$refs.slotContainer.innerHTML = "";
      this.$refs.slotContainer.append(document.createElement("slot"));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.table {
  border-collapse: collapse;
}
.table tr {
  border-bottom: 1px solid #e8e8e8;
}
.table th {
  padding: 16px 8px 18px;
}
.table thead {
  background-color: #fafafa;
}
</style>
