
  
<template>
  <div class="dropdown" v-if="options">
    <input
      class="dropdown-input"
      :name="name"
      @focus="showOptions()"
      @blur="exit()"
      @keyup="keyMonitor"
      v-model="searchFilter"
      :placeholder="placeholder"
    />
    <div class="dropdown-content" v-show="optionsShown">
      <div
        class="dropdown-item"
        @mousedown="selectOption(option)"
        v-for="(option, index) in filteredOptions"
        :key="index"
      >{{ option.name || option.id || '-' }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dropdown",
  template: "Dropdown",
  props: {
    name: {
      type: String,
      required: false,
      default: "dropdown"
    },
    options: {
      type: Array,
      required: true,
      default: () => []
    },
    placeholder: {
      type: String,
      required: false,
      default: "Selecciona una opción"
    },
    maxItem: {
      type: Number,
      required: false,
      default: 6
    }
  },
  data() {
    return {
      selected: {},
      optionsShown: false,
      searchFilter: ""
    };
  },
  created() {
    this.$emit("selected", this.selected);
  },
  computed: {
    filteredOptions() {
      const filtered = [];
      const regOption = new RegExp(this.searchFilter, "ig");
      for (const option of this.options) {
        if (this.searchFilter.length < 1 || option.name.match(regOption)) {
          if (filtered.length < this.maxItem) filtered.push(option);
        }
      }
      return filtered;
    }
  },
  methods: {
    selectOption(option) {
      this.selected = option;
      this.optionsShown = false;
      this.searchFilter = this.selected.name;
      this.$emit("selected", this.selected);
    },
    showOptions() {
      this.searchFilter = "";
      this.optionsShown = true;
    },
    exit() {
      if (!this.selected.id) {
        this.selected = {};
        this.searchFilter = "";
      } else {
        this.searchFilter = this.selected.name;
      }
      this.$emit("selected", this.selected);
      this.optionsShown = false;
    },
    keyMonitor: function(event) {
      if (event.key === "Enter" && this.filteredOptions[0])
        this.selectOption(this.filteredOptions[0]);
    }
  },
  watch: {
    searchFilter() {
      if (this.filteredOptions.length === 0) {
        this.selected = {};
      } else {
        this.selected = this.filteredOptions[0];
      }
      this.$emit("filter", this.searchFilter);
    }
  },
  mounted() {
    console.log("recibe", this.options);
  }
};
</script>

<style scoped>
.dropdown-input {
  background: #fff;
  cursor: pointer;
  border: 1px solid #e7ecf5;
  border-radius: 3px;
  color: #333;
  display: block;
  font-size: 0.8em;
  padding: 6px;
  width: -webkit-fill-available;
  width: 96%;
}
.dropdown-content {
  position: absolute;
  background-color: #fff;
  border: 1px solid #e7ecf5;
  box-shadow: 0px -8px 34px 0px rgba(0, 0, 0, 0.05);
  overflow: auto;
  z-index: 1;
}

.dropdown-item {
  color: black;
  font-size: 0.7em;
  line-height: 1em;
  padding: 8px;
  text-decoration: none;
  display: block;
  cursor: pointer;
}

.dropdown-item:hover {
  background-color: #b8eae3;
}
</style>



