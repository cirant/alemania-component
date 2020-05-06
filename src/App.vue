<template>
  <div id="app">
    <div>
      <Typography variant="h4" weight="bold" type="primary">DIAGNÓSTICO</Typography>
      <Typography variant="span" size="12">Última actualización: 10 / 07 / 2017, 20:30 hrs.</Typography>
    </div>
    <Table>
      <thead>
        <tr>
          <th>
            <input type="checkbox" />
          </th>
          <th>nombre del diagnóstico</th>
          <th>estado</th>
          <th>fecha</th>
          <td colspan="2"></td>
          <th>acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td align="center">
            <input type="checkbox" />
          </td>
          <td>
            <Typography
              variant="p"
              type="primary"
            >Afecciones respiratorias debidas a inhalación de gases, humos…</Typography>
          </td>
          <td>
            <Status value="confirmado" />
          </td>
          <td>
            <Typography>2014-12-24 24:15:00</Typography>
          </td>
          <td>
            <Typography weight="bold">ENO</Typography>
          </td>
          <td>
            <Typography weight="bold">GES</Typography>
          </td>
          <td>
            <div class="actions-container">
              <Buttom variant="text" icon="edit">Editar</Buttom>
              <Buttom variant="text" color="error" icon="trash">Eliminar</Buttom>
            </div>
          </td>
        </tr>
      </tbody>
    </Table>
    <table class="table">
      <thead>
        <tr>
          <th>
            <input type="checkbox" />
          </th>
          <th>nombre del diagnóstico</th>
          <th>estado</th>
          <th>fecha</th>
          <th>acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            <input type="checkbox" />
          </td>
          <td>
            <Typography
              variant="p"
              type="primary"
            >Afecciones respiratorias debidas a inhalación de gases, humos…</Typography>
          </td>
          <td>
            <Status value="confirmado" />
          </td>
          <td>
            <Typography>2014-12-24 24:15:00</Typography>
          </td>
          <td>
            <Typography weight="bold">ENO</Typography>
          </td>
          <td>
            <Typography weight="bold">GES</Typography>
          </td>
          <td>
            <div class="actions-container">
              <Buttom variant="text" icon="edit">Editar</Buttom>
              <Buttom variant="text" color="error" icon="trash">Eliminar</Buttom>
            </div>
          </td>
        </tr>
        <tr>
          <td>
            <input type="checkbox" />
          </td>
          <td>
            <Typography
              variant="p"
              type="primary"
            >Afecciones respiratorias debidas a inhalación de gases, humos…</Typography>
          </td>
          <td>
            <Status value="sospecha" />
          </td>
          <td>
            <Typography>2014-12-24 24:15:00</Typography>
          </td>
          <td>
            <Typography weight="bold">ENO</Typography>
          </td>
          <td>
            <Typography weight="bold">GES</Typography>
          </td>
          <td>
            <div class="actions-container">
              <Buttom variant="text" icon="edit">Editar</Buttom>
              <Buttom variant="text" color="error" icon="trash">Eliminar</Buttom>
            </div>
          </td>
        </tr>
        <tr>
          <td>
            <input type="checkbox" />
          </td>
          <td>
            <Typography
              variant="p"
              type="primary"
            >Afecciones respiratorias debidas a inhalación de gases, humos…</Typography>
          </td>
          <td>
            <Status />
          </td>
          <td>
            <Typography>2014-12-24 24:15:00</Typography>
          </td>
          <td>
            <Typography weight="bold">ENO</Typography>
          </td>
          <td>
            <Typography weight="bold">GES</Typography>
          </td>
          <td>
            <div class="actions-container">
              <Buttom variant="text" icon="edit">Editar</Buttom>
              <Buttom variant="text" color="error" icon="trash">Eliminar</Buttom>
            </div>
          </td>
        </tr>
      </tbody>
    </table>

    <Buttom @onClick="mainClick()">Nuevo Diagnóstico</Buttom>

    <br />

    <div class="flex">
      Typography
      <Typography variant="h1">text h1 - h6</Typography>
      <Typography variant="h1" size="16">text h6</Typography>
      <Typography variant="p">text p</Typography>
      <Typography variant="p" weight="bold">text bold</Typography>
      <Typography variant="p" weight="lighter">text lighter</Typography>
      <Typography variant="p">text normal</Typography>
      <Typography type="primary">primary color</Typography>
      <Typography type="error">error color</Typography>
    </div>
    <div class="flex">
      Button
      <Buttom>Default</Buttom>
      <Buttom color="error">Error</Buttom>
      <Buttom variant="text">Default text button</Buttom>
      <Buttom variant="text" color="error">Error text button</Buttom>
      <Buttom variant="text" icon="edit">icon edit</Buttom>
      <Buttom variant="text" color="error" icon="trash">icon trash</Buttom>
    </div>

    <br />

    <Modal v-if="showModal">
      <div slot="body">
        <Select :options="options" />

        <NotificationTag type="exito" />
        <NotificationTag type="informacion" />
        <NotificationTag type="alerta" />
      </div>
    </Modal>
    <Buttom @onClick="showModal = true">Default</Buttom>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Buttom from "./components/Button.vue";

import Typography from "./components/Typography";
import Select from "./components/Select";
import Status from "./components/Status";
import Table from "./components/Table";
import Modal from "./components/Modal";
import NotificationTag from "./components/NotificationTag";

export default {
  name: "App",
  components: {
    Buttom,
    Typography,
    Select,
    Status,
    Table,
    Modal,
    NotificationTag
  },
  methods: {
    mainClick() {
      console.log("este es un main click");
    }
  },
  data() {
    return {
      showModal: false,
      options: [
        { id: 1, name: "Trombosis profunda" },
        { id: 2, name: "Trombosis mega profunda" },
        { id: 3, name: "Hiper mega Trombosis" }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.table {
  width: 100%;
  margin-bottom: 35px;
}
.flex {
  display: inline-flex;
  flex-direction: column;
  padding: 8px;
}
</style>
