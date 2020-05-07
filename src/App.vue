<template>
  <div id="app">
    <div :key="index" v-for="(data, index) in tableData.body">{{data.content}}</div>
    <Card align="left">
      <div>
        <Typography variant="h4" weight="bold" type="primary">DIAGNÓSTICO</Typography>
        <Typography variant="span" size="12">Última actualización: 10 / 07 / 2017, 20:30 hrs.</Typography>
      </div>
      <Table :columns="tableData.headers" :rows="tableData.body"></Table>
      <TableDiagnostico
        :allClick="allClick"
        :clickOne="rowClick"
        :columns="tableDiagnostico.headers"
        :rows="tableDiagnostico.body"
      ></TableDiagnostico>
      <table class="table"></table>
      <Buttom @onClick="mainClick">Nuevo Diagnóstico</Buttom>
    </Card>
    <br />
    <Card align="left">
      <div class="flex">
        <Typography variant="h1" weight="bold" size="16">Typography</Typography>
        <br />
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
        <Typography variant="h1" weight="bold" size="16">Button</Typography>
        <Buttom>Default</Buttom>
        <Buttom color="error">Error</Buttom>
        <Buttom variant="text">Default text button</Buttom>
        <Buttom variant="text" color="error">Error text button</Buttom>
        <Buttom variant="text" icon="edit">icon edit</Buttom>
        <Buttom variant="text" color="error" icon="trash">icon trash</Buttom>
      </div>
      <div class="flex">
        <Typography variant="h1" weight="bold" size="16">Status</Typography>
        <Status value="sospecha" />
        <Status value="confirmado" />
        <Status value />
      </div>
    </Card>

    <Modal v-if="showModal" @closeModal="closeModal()">
      <div slot="body">
        <Select :options="options" />

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
        <TextArea />
      </div>
    </Modal>
    <Buttom @onClick="showModal = true">Default</Buttom>
  </div>
</template>

<script>
import Buttom from "./components/Button.vue";
import Typography from "./components/Typography";
import Select from "./components/Select";
import Status from "./components/Status";
import Table from "./components/Table";
import Modal from "./components/Modal";
import NotificationTag from "./components/NotificationTag";
import TableDiagnostico from "./components/TableDiagnostico";
import TextArea from "./components/TextArea";
import Card from "./components/Card";
export default {
  name: "App",
  components: {
    Buttom,
    Typography,
    Select,
    Status,
    Table,
    Modal,
    NotificationTag,
    TableDiagnostico,
    TextArea,
    Card
  },
  data: function() {
    return {
      tableData: {
        headers: {
          checkbox: "",
          diagnostico: "Nombre del diagnóstico",
          fecha: "Fecha",
          estado: "Estado",
          eno: "",
          ges: "",
          acciones: ""
        },
        body: [
          {
            checkboxArea: "active",
            diagnostico:
              "Afecciones respiratorias debidas a inhalación de gases, humos…",
            estado: "confirmado",
            fecha: "Fecha",
            eno: "ENO",
            ges: "GES",
            acciones: "xxxxxx"
          }
        ]
      },
      tableDiagnostico: {
        headers: {
          checkbox: false,
          diagnostico: "Nombre del diagnóstico",
          estado: "Estado",
          fecha: "Fecha",
          eno: "",
          ges: "",
          acciones: "acciones"
        },
        body: [
          {
            checkbox: false,
            diagnostico: {
              variant: "p",
              type: "primary",
              text:
                "Afecciones respiratorias debidas a inhalación de gases, humos…"
            },
            estado: "confirmado",
            fecha: {
              size: "",
              text: "2014-12-24  24:15:00"
            },
            eno: {
              weight: "bold",
              text: "ENO"
            },
            ges: {
              weight: "bold",
              text: "GES"
            },
            acciones: [
              {
                text: "Editar",
                variant: "text",
                icon: "edit",
                onClick: function() {
                  console.log("hola mundo Editar");
                }
              },
              {
                text: "Eliminar",
                variant: "text",
                color: "error",
                icon: "trash",
                onClick: function() {
                  console.log("hola mundo eliminar");
                }
              }
            ]
          },
          {
            checkbox: false,
            diagnostico: {
              variant: "p",
              type: "primary",
              text:
                "Afecciones respiratorias debidas a inhalación de gases, humos…"
            },
            estado: "",
            fecha: {
              size: "",
              text: "2014-12-24  24:15:00"
            },
            eno: {
              weight: "bold",
              text: "ENO"
            },
            ges: {
              weight: "bold",
              text: "GES"
            },
            acciones: [
              {
                text: "Editar",
                variant: "text",
                icon: "edit",
                onClick: function() {
                  console.log("hola mundo Editar");
                }
              },
              {
                text: "Eliminar",
                variant: "text",
                color: "error",
                icon: "trash",
                onClick: function() {
                  console.log("hola mundo eliminar");
                }
              }
            ]
          },
          {
            checkbox: false,
            diagnostico: {
              variant: "p",
              type: "primary",
              text:
                "Afecciones respiratorias debidas a inhalación de gases, humos…"
            },
            estado: "sospecha",
            fecha: {
              size: "",
              text: "2014-12-24  24:15:00"
            },
            eno: {
              weight: "bold",
              text: "ENO"
            },
            ges: {
              weight: "bold",
              text: "GES"
            },
            acciones: [
              {
                text: "Editar",
                variant: "text",
                icon: "edit",
                onClick: function() {
                  console.log("hola mundo Editar");
                }
              },
              {
                text: "Eliminar",
                variant: "text",
                color: "error",
                icon: "trash",
                onClick: function() {
                  console.log("hola mundo eliminar");
                }
              }
            ]
          }
        ]
      },
      showModal: false,
      options: [
        { id: 1, name: "Trombosis profunda" },
        { id: 2, name: "Trombosis mega profunda" },
        { id: 3, name: "Hiper mega Trombosis" }
      ]
    };
  },
  methods: {
    mainClick() {
      console.log("este es un main click");
    },
    rowClick(position, status) {
      console.log("este es un main click", position, status);
      console.log(
        "this.$data.tableDiagnostico.body[position]",
        this.tableDiagnostico.body[position].checkbox
      );

      this.tableDiagnostico.body[position].checkbox = status;
    },
    allClick(e) {
      console.log("click en todos", e);
      this.tableDiagnostico.headers.checkbox = e;
      this.tableDiagnostico.body.forEach(element => {
        element.checkbox = e;
      });
    },
    closeModal() {
      this.showModal = false;
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
.flex {
  display: inline-flex;
  flex-direction: column;
  padding: 8px;
}
</style>
