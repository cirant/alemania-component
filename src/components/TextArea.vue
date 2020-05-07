<template>
  <div class="textAreaContainer">
    <textarea class="textArea" v-model="text" :change="handlerChange()" />
  </div>
</template>

<script>
export default {
  name: "textArea",
  props: {
    name: {
      type: String,
      default: "input"
    }
  },
  data() {
    return {
      text: ""
    };
  },
  methods: {
    handlerChange() {
      this.$emit("textUpdated", this.text);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.textArea {
  resize: none;
  width: stretch;
  height: 62px;
  border-radius: 4px;
  border: solid 1px #d9d9d9;
}
</style>
