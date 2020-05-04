<template>
  <div class="card" ref="slotContainer"></div>
</template>

<script>
export default {
  name: "Card",
  mounted() {
    console.log("aqui ");
    this.$nextTick().then(this.fixSlot.bind(this));
  },
  methods: {
    // This is where the magic happens
    fixSlot() {
      // remove all the innerHTML that vue has place where the slot should be
      this.$refs.slotContainer.innerHTML = "";
      // // replace it with a new slot, if you are using named slot you can just add attributes to the slot
      this.$refs.slotContainer.append(document.createElement("slot"));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scss scoped>
.card {
  background-color: white;
  border-radius: 4px;
  box-shadow: 0px 2px 4px #9da0a4;
  padding: 16px 36px;
}
</style>
