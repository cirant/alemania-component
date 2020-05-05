<template>
  <button
    class="btn"
    :type="type"
    v-bind:class="{
      btnSolid: variant === 'contained',
      btnText: variant === 'text',
      color: color === 'primary',
      error: color === 'error'
    }"
    @click="$emit('onClick')"
  >
    <slot />

    <span v-if="icon ==='edit'" class="icon">
      <svg
        aria-hidden="true"
        focusable="false"
        data-prefix="fal"
        data-icon="pencil"
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 512 512"
        class="svg-inline--fa fa-pencil fa-w-16"
      >
        <path
          fill="currentColor"
          d="M493.255 56.236l-37.49-37.49c-24.993-24.993-65.515-24.994-90.51 0L12.838 371.162.151 485.346c-1.698 15.286 11.22 28.203 26.504 26.504l114.184-12.687 352.417-352.417c24.992-24.994 24.992-65.517-.001-90.51zm-95.196 140.45L174 420.745V386h-48v-48H91.255l224.059-224.059 82.745 82.745zM126.147 468.598l-58.995 6.555-30.305-30.305 6.555-58.995L63.255 366H98v48h48v34.745l-19.853 19.853zm344.48-344.48l-49.941 49.941-82.745-82.745 49.941-49.941c12.505-12.505 32.748-12.507 45.255 0l37.49 37.49c12.506 12.506 12.507 32.747 0 45.255z"
          class
        />
      </svg>
    </span>

    <span v-if="icon ==='trash'" class="icon">
      <svg
        aria-hidden="true"
        focusable="false"
        data-prefix="far"
        data-icon="trash-alt"
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 448 512"
        class="svg-inline--fa fa-trash-alt fa-w-14"
      >
        <path
          fill="currentColor"
          d="M268 416h24a12 12 0 0 0 12-12V188a12 12 0 0 0-12-12h-24a12 12 0 0 0-12 12v216a12 12 0 0 0 12 12zM432 80h-82.41l-34-56.7A48 48 0 0 0 274.41 0H173.59a48 48 0 0 0-41.16 23.3L98.41 80H16A16 16 0 0 0 0 96v16a16 16 0 0 0 16 16h16v336a48 48 0 0 0 48 48h288a48 48 0 0 0 48-48V128h16a16 16 0 0 0 16-16V96a16 16 0 0 0-16-16zM171.84 50.91A6 6 0 0 1 177 48h94a6 6 0 0 1 5.15 2.91L293.61 80H154.39zM368 464H80V128h288zm-212-48h24a12 12 0 0 0 12-12V188a12 12 0 0 0-12-12h-24a12 12 0 0 0-12 12v216a12 12 0 0 0 12 12z"
          class
        />
      </svg>
    </span>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    type: {
      type: String,
      default: "button"
    },
    variant: {
      type: String,
      default: "contained"
    },
    color: {
      type: String,
      default: "primary"
    },
    icon: {
      type: String
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn {
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  cursor: pointer;
  font-size: 14px;
}
.icon {
  width: 15px;
  display: inline-block;
  margin-left: 4px;
  vertical-align: middle;
}

.btnSolid {
  background-color: #01ccad;
  color: white;
}

.btnSolid.error {
  background-color: #e82037;
}

.btnText {
  color: #01ccad;
  background-color: transparent;
}

.btnText.error {
  color: #e82037;
}
</style>
