<template>
  <b-card no-body bg-variant="secondary" text-variant="white" class="text-center">
    <b-row>
      <b-col class="custom-header-title">
        <b-card-header class="h-100" :header="title.toUpperCase()"/>
      </b-col>
      <b-col class="m-4">
        <router-link :to="{name: routeName}">
          <i :class="'fas fa-' + iconName + ' fa-5x'"></i>
        </router-link>
      </b-col>
    </b-row>
  </b-card>
</template>

<script>
export default {
  name: "AdminOptionBox",
  props: ["routeName", "iconName", "title"]
};
</script>

<style scoped>
.custom-header-title {
  margin: auto 0;
}
</style>
