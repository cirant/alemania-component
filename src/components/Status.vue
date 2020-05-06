<template>
  <div class="btn" @click="$emit('onClick')">
    <span
      class="circle"
      v-bind:class="{
      confirm: value === 'confirmado',
      negative: value === 'sospecha',
    }"
    ></span>

    <span class="text" v-if="value === 'confirmado'">Confirmado</span>
    <span class="text" v-else-if="value === 'sospecha'">Sospecha</span>
    <span class="text" v-else>Descartado</span>
  </div>
</template>

<script>
export default {
  name: "Status",
  props: ["value"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.circle {
  width: 6px;
  height: 6px;
  display: inline-block;
  border-radius: 100%;
  background-color: rgba(0, 0, 0, 0.25);
}

.text {
  padding-left: 8px;
  font-size: 14px;
  font-family: Helvetica, Arial, sans-serif;
}

.confirm {
  background-color: #009bde;
}

.negative {
  background-color: #e82037;
}
</style>
