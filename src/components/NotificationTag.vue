<template>
  <div
    @click="$emit('onClick')"
    class="container"
    v-bind:class="{
      succes: type === 'exito',
      info: type === 'informacion',
      warning: type === 'alerta'
    }"
  >
    <div class="messageContainer">
      <span class="icon">
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
      <div class="slotMessage">
        <slot name="message">
          <p>mensajes</p>
        </slot>
      </div>
    </div>

    <div class="actionContainer">
      <slot name="action"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "NotificationTag",
  props: {
    type: {
      type: String,
      required: false,
      default: "exito"
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
}

.container.succes {
  border: solid 1px #b7eb8f;
  background-color: #f6ffed;
}

.container.info {
  border: solid 1px #91d5ff;
  background-color: #e6f7ff;
}
.container.warning {
  border: solid 1px #ffe58f;
  background-color: #fffbe6;
}
.slotMessage {
  display: inline-block;
}
.icon {
  width: 15px;
  display: inline-block;
  margin-left: 4px;
  vertical-align: middle;
}

/* .slotMessage {
 
} */
/* .messageContainer {
  display: inline-block;
} */
</style>
