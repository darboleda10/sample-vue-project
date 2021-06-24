<template>
  <div class="component">
    <div class="container--fluid component-container">
      <h1>Drivers</h1>
      <ListViewComponent :items="result" v-if="!loading && result" />
      <v-progress-circular
        v-if="loading"
        indeterminate
        color="primary"
      ></v-progress-circular>
    </div>
  </div>
</template>

<script type="text/babel">
import DriversService from "@/services/drivers";
import ListViewComponent from "../../components/list-view-component/list-view-component.vue";

export default {
  name: "views-orders-index",
  watch: {},
  props: {},
  data() {
    return {
      result: undefined,
      loading: Boolean,
    };
  },
  methods: {
    getDrivers() {
      this.loading = true;
      return DriversService.getDrivers().then((result) => {
        this.result = result;
        this.loading = false;
      });
    },
  },
  computed: {},
  created() {},
  mounted() {
    this.getDrivers();
  },
  beforeDestroy() {},
  mixins: [],
  components: {
    ListViewComponent,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h1 {
  margin-left: 10px;
}
.v-progress-circular {
  display: flex;
  align-self: center;
  margin: auto !important;
}
.component-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
