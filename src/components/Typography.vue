<template>
  <h1
    class="root main-styles"
    v-if="variant == 'h1'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h1>
  <h2
    class="root main-styles"
    v-else-if="variant == 'h2'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h2>
  <h3
    class="root main-styles"
    v-else-if="variant == 'h3'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h3>
  <h4
    class="root main-styles"
    v-else-if="variant == 'h4'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h4>
  <h5
    class="root main-styles"
    v-else-if="variant == 'h5'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h5>
  <h6
    class="root main-styles"
    v-else-if="variant == 'h6'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </h6>
  <p
    class="root main-styles"
    v-else-if="variant == 'p'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </p>
  <span
    class="root main-styles"
    v-else-if="variant == 'span'"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </span>
  <div
    v-else
    class="root main-styles"
    v-bind:class="{
      fontBold: weight === 'bold',
      primary: type === 'primary',
      error: type === 'error',
      font16: size === '16',
      font12: size === '12',
      fontLighter: weight === 'lighter'
    }"
  >
    <slot />
  </div>
</template>

<script>
export default {
  name: "Typography",
  props: ["weight", "variant", "type", "size"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.root {
  display: inline;
  margin: 0px;
  font-size: 14px;
  font-family: Helvetica, Arial, sans-serif;
}
.main-styles {
  font-weight: inherit;
  font-family: Helvetica, Arial, sans-serif;
}

.font16 {
  font-size: 16px;
}
.font12 {
  font-size: 12px;
}
.primary {
  color: #01ccad;
}
.error {
  color: #ff4c4c;
}
.fontBold {
  font-weight: bold;
}
.font-normal {
  font-weight: normal;
}
.fontLighter {
  font-weight: lighter;
}
</style>
