<template>
  <div class="card">
    <slot />
  </div>
</template>

<script>
export default {
  name: "Card"
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
