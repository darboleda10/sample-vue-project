<template>
  <div>
    <v-list-item
      v-for="(item, i) in items"
      :key="i"
      class="row-item"
      @click="viewDetails(item)"
    >
      <v-list-item-icon>
        <AvatarComponent
          :avatarColor="'green'"
          :avatarText="getAvatarText(item.first_name, item.last_name)"
        />
      </v-list-item-icon>
      <v-list-item-content>
        <v-list-item-title v-text="item.first_name"></v-list-item-title>
      </v-list-item-content>
    </v-list-item>
  </div>
</template>

<script>
import AvatarComponent from "../avatar-component/avatar-component.vue";
export default {
  name: "ListViewComponent",
  data: () => ({}),
  props: {
    items: Array,
  },
  components: {
    AvatarComponent,
  },
  methods: {
    getAvatarText(firstName, lastName) {
      let initials = "";
      if (firstName) {
        initials = firstName.substr(0, 1);
      }
      if (lastName) {
        initials += "" + lastName.substr(0, 1);
      }
      return initials;
    },
    viewDetails(driver) {
      const selectedDriver = {
        id: driver.id,
        firstName: driver.first_name,
        lastName: driver.last_name,
      };
      this.$router.push({
        name: "driver-details",
        params: { id: selectedDriver.id, driverInfo: selectedDriver },
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.row-item {
  border: 1px solid gray;
  border-radius: 10px;
  margin: 0 10px 5px 10px;
}
.row-item:hover {
  border: 2px solid blue;
  cursor: pointer;
}
</style>