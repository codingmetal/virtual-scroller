<template>
  <div id="app">
    <virtual-scroller :list="tableData" key-field="id" :item-height="38" v-slot="{ item, index, pos }">
      <p>{{`index: ${index}, pos: ${pos}, name: ${item.text}`}}</p>
    </virtual-scroller>
  </div>
</template>

<script>
  import VirtualScroller from "./components/VirtualScroller";

  export default {
    name: "App",
    components: {
      VirtualScroller,
    },
    data() {
      return {
        tableData: [],
      };
    },
    methods: {
      buildData() {
        let temp = [];
        for (let i = 0; i < 1000; i++) {
          let obj = {};
          obj.text = `row${i + 1}`;
          obj.id = i;
          temp.push(obj);
        }
        return temp;
      },
    },
    created() {
      this.tableData = this.buildData();
    },
    mounted() {
    }
  };
</script>

<style>
  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    height: 500px;
  }
</style>