<template>
  <button class="btn-custom" @click="$emit('add')">
    <slot />
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    msg: String
  },
  methods: {
    clickme() {
      console.log("clicked");
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn-custom {
  padding: 8px 16px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
