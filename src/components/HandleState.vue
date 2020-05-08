<template>
  <Status v-if="!editing" :value="elementValue" />
  <Select v-else :options="options" @selected="updateSelector" />
</template>

<script>
import Status from "./Status";
import Select from "./Select";

export default {
  name: "HandleState",
  components: {
    Status,
    Select
  },
  data() {
    return {
      ownValue: "",
      options: [
        { id: 3, name: "Sospecha" },
        { id: 1, name: "Alta" },
        { id: 2, name: "Confirmado" },
        { id: 4, name: "Descartado" }
      ]
    };
  },
  props: {
    editing: {
      type: Boolean,
      default: false
    },
    currentValue: {
      type: String,
      default: "sospecha"
    },
    index: {
      type: Number,
      default: 0
    }
  },
  methods: {
    updateSelector(value) {
      this.ownValue = value.name.toLocaleLowerCase();
      sessionStorage.setItem(`status-${this.index}`, value.name);
    }
  },
  computed: {
    elementValue() {
      const prevCache = sessionStorage.getItem(`status-${this.index}`);
      if (this.ownValue !== "") return this.ownValue;
      else if (prevCache !== null) return prevCache.toLowerCase();
      else return this.currentValue;
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
  font-family: Helvetica, Arial, sans-serif;
  position: relative;
  overflow: hidden;
  white-space: nowrap;
}
.btn:active::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  left: 0;
  top: 0;
  background-color: rgba(0, 0, 0, 0.1);
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

.btnOutlined {
  border: 1px solid #d9d9d9;
  color: #000000a6;
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

.btnText.secondary {
  color: #00000040;
}
</style>
