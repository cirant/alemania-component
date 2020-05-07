
  
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
            <div class="selection-container" v-if="userIsSelecting">
              <Select @selected="updateSelector" :options="options" />
              <div class="notifications" v-if="showNotifications">
                <NotificationTag type="informacion">
                  <Typography variant="p" slot="message" size="12">Patología GES.</Typography>
                  <Typography variant="p" slot="action" size="12">Revisar</Typography>
                </NotificationTag>

                <NotificationTag type="alerta">
                  <Typography
                    variant="p"
                    slot="message"
                    size="12"
                  >Este diagnóstico está clasificado como ENO, notificar.</Typography>
                  <Typography variant="p" slot="action" size="12">x</Typography>
                </NotificationTag>
              </div>
              <div>
                <Typography>Problema de salud:</Typography>
                <TextArea @textUpdated="updateTextField" />
              </div>
            </div>
            <div class="result-container" v-else>
              <NotificationTag type="exito">
                <div slot="message">
                  <Typography variant="h1" weight="bold">Diagnóstico agregado</Typography>
                  <br />
                  <Typography
                    variant="p"
                    size="12"
                  >El diagnóstico fue agregado exitosamente, indicar estado de diagnóstico en el listado.</Typography>
                </div>
              </NotificationTag>
            </div>
          </div>

          <div class="modal-footer">
            <slot name="footer">
              <div v-if="userIsSelecting">
                <Buttom variant="outlined" @onClick="closeModal()">Cancelar</Buttom>
                <Buttom @onClick="addHealthCondition()">Agregar</Buttom>
              </div>
              <div v-else>
                <Buttom @onClick="endProcess()">Ir a la ficha</Buttom>
              </div>
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
import Select from "./Select";
import TextArea from "./TextArea";
import NotificationTag from "./NotificationTag";

export default {
  name: "Modal",
  components: {
    Buttom,
    Typography,
    Select,
    TextArea,
    NotificationTag
  },
  methods: {
    closeModal() {
      this.$emit("closeModal");
    },
    updateSelector(e) {
      this.selectedOption = e;
      this.showNotifications = false;
      if (e.type === "GES" || e.type === "ENO") {
        setTimeout(() => (this.showNotifications = true), 500);
      }
    },
    updateTextField(e) {
      this.healthCondition = e;
    },
    addHealthCondition() {
      const dataToSend = {
        medicalDiagnostic: this.selectedOption,
        description: this.healthCondition
      };
      this.$emit("endProcess", dataToSend);

      setTimeout(() => (this.userIsSelecting = false), 500);
    },
    endProcess() {
      this.closeModal();
    }
  },
  data: function() {
    return {
      options: [
        { id: 1, name: "Trombosis profunda", type: "GES" },
        { id: 2, name: "Trombosis mega profunda", type: "ENO" },
        { id: 3, name: "Hiper mega Trombosis", type: "ENO" },
        { id: 3, name: "Otra info", type: "GES" }
      ],
      showNotifications: false,
      userIsSelecting: true,
      selectedOption: "",
      healthCondition: ""
    };
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



