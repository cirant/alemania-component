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
      <baseIcon v-if="type === 'exito'" icon-name="edit" viewBox="0 0 24 24" height="18" width="18">
        <Succes />
      </baseIcon>
      <baseIcon v-else-if="type === 'alerta'" icon-name="edit" viewBox="0 0 14 14">
        <Warning />
      </baseIcon>
      <baseIcon v-else icon-name="edit" viewBox="0 0 14 14">
        <Info />
      </baseIcon>

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
import BaseIcon from "./BaseIcon";
import Succes from "./Icons/Succes";
import Warning from "./Icons/Warning";
import Info from "./Icons/Info";
export default {
  name: "NotificationTag",
  components: {
    BaseIcon,
    Succes,
    Warning,
    Info
  },
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
  padding: 9px;
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
  text-align: left;
}
.icon {
  width: 15px;
  display: inline-block;
  margin-left: 4px;
  vertical-align: middle;
}

.messageContainer {
  display: flex;
}
</style>
