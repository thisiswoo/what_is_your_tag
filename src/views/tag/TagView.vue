<template>
  <div class="tag tag-div">
    <h1>This is an Tag page</h1>
    <ContainerView />
    <ContainerTagView />
  </div>
</template>

<script>
import ContainerView from "../../components/layouts/ContainerView.vue";
import ContainerTagView from "../../components/layouts/ContainerTagView.vue";

export default {
  name: "TagView",
  components: {
    ContainerView,
    ContainerTagView,
  },
};
</script>

<style lang="scss">
@import "../../assets/style/scss/tagView.scss";
</style>
