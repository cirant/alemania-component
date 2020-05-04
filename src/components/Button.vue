<template>
  <button class="btn" @click="$emit('click')">
    <slot />
  </button>
</template>

<script>
export default {
  name: "Button"
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  background-color: #01ccad;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
}
</style>
