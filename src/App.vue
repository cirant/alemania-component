<template>
  <div id="app">
    <Card>
      <div>
        <Typography variant="h4" weight="bold" type="primary">DIAGNÓSTICO</Typography>
        <Typography variant="span">Última actualización: 10 / 07 / 2017, 20:30 hrs.</Typography>
      </div>
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
            <td>Afecciones respiratorias debidas a inhalación de gases, humos…</td>
            <td>confirmado</td>
            <td>2014-12-24 24:15:00</td>
            <td>ENO</td>
            <td>GES</td>
            <td>
              <div class="actions-container">
                <button>Editar</button>
                <button>Eliminar</button>
              </div>
            </td>
          </tr>
        </tbody>
      </table>

      <Buttom @onClick="mainClick()">Nuevo Diagnóstico</Buttom>
    </Card>
    <br />
    <Card align="left">
      <Typography variant="h1">text h1</Typography>
      <br />
      <Typography variant="h2">text h2</Typography>
      <br />
      <Typography variant="h3">text h3</Typography>
      <br />
      <Typography variant="h4">text h4</Typography>
      <br />
      <Typography variant="h5">text h5</Typography>
      <br />
      <Typography variant="h6">text h6</Typography>
      <br />
      <Typography variant="p">text p</Typography>
      <br />
      <Typography variant="p" weight="bold">text bold</Typography>
      <br />
      <Typography variant="p" weight="lighter">text lighter</Typography>
      <br />
      <Typography variant="p">text normal</Typography>
      <br />
      <Typography type="primary">primary color</Typography>
      <br />
      <Typography type="error">error color</Typography>
      <br />
    </Card>
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Buttom from "./components/Button.vue";
import Card from "./components/Card";
import Typography from "./components/Typography";

export default {
  name: "App",
  components: {
    Card,
    Buttom,
    Typography
  },
  methods: {
    mainClick() {
      console.log("este es un main click");
    }
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
</style>
