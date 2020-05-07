
  
<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper" @click="closeModal()">
        <div class="modal-container" @click.stop>
          <div class="modal-header">
            <slot name="header">
              <Typography type="primary" weight="bold">Nuevo Diagnóstico</Typography>
              <Buttom variant="text" color="secondary" @onClick="closeModal()">x</Buttom>
            </slot>
          </div>

          <div class="modal-body">
            <slot name="body">default body</slot>
          </div>

          <div class="modal-footer">
            <slot name="footer">
              <Buttom variant="outlined" @onClick="closeModal()">Cancelar</Buttom>
              <Buttom @onClick="closeModal()">Agregar</Buttom>
            </slot>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import Buttom from "./Button.vue";
import Typography from "./Typography";

export default {
  name: "Modal",
  components: {
    Buttom,
    Typography
  },
  mounted() {
    console.log("==============================");
    if (process.env.NODE_ENV !== "development") {
      this.$nextTick().then(this.fixSlot.bind(this));
    }
  },
  methods: {
    closeModal() {
      this.$emit("closeModal");
    },
    fixSlot() {
      this.$refs.slotContainer.innerHTML = "";
      this.$refs.slotContainer.append(document.createElement("slot"));
    }
  }
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 400px;
  margin: 0px auto;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

.modal-header {
  border-bottom: 1px solid rgba(0, 0, 0, 0.09);
  min-height: 56px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
}

.modal-footer {
  border-top: 1px solid rgba(0, 0, 0, 0.09);
  min-height: 56px;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.modal-body {
  margin: 20px 0;
  padding: 26px 18px;
}

.modal-default-button {
  float: right;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>



