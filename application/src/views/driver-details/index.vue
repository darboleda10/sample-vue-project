<template>
  <div>
    <div v-show="!loading && driver">
      <div class="back-link" @click="navigateBack()">
        <p>Back to Drivers</p>
      </div>
      <div>
        <h3>Driver Info</h3>
        <p>ID: {{ driver.id }}</p>
        <p>First Name: {{ driver.firstName }}</p>
        <p>Last Name: {{ driver.lastName }}</p>
      </div>
    </div>
    <div v-show="loading && !driver">
      <v-progress-circular indeterminate color="primary"></v-progress-circular>
    </div>
  </div>
</template>

<script>
export default {
  name: "DriverDetails",
  data() {
    return {
      result: undefined,
      driver: Object,
      loading: Boolean,
    };
  },
  methods: {
    navigateBack() {
      this.$router.push({ name: "drivers-index" });
    },
  },
  created() {
    this.loading = true;
    this.driver = this.$route.params.driverInfo;
    this.loading = false;
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.back-link {
  display: flex;
  flex-direction: column;
  cursor: pointer;
}
div {
  margin: 10px 0 10px 10px;
}
.v-progress-circular {
  display: flex;
  align-self: center;
  margin: auto !important;
}
</style>