<template>
    <v-avatar
      :color="avatarColor"
      size="48"
    >
      <span class="white--text text-h5">{{avatarText}}</span>
    </v-avatar>
</template>

<script>
export default {
  name: "AvatarComponent",
  data: () => ({
  }),
  props: {
    avatarText: String,
    avatarColor: String
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>