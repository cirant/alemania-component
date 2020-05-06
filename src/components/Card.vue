<template>
  <div class="card" ref="slotContainer">
    <slot />
  </div>
</template>

<script>
export default {
  name: "Card",
  mounted() {
    console.log("==============================");
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
<style scss scoped>
.card {
  background-color: white;
  border-radius: 4px;
  box-shadow: 0px 2px 4px #9da0a4;
  padding: 23px 46px;
  width: 100%;
  text-align: left;
  box-sizing: border-box;
  font-family: Helvetica, Arial, sans-serif;
}
</style>
