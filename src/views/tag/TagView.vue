<template>
  <div class="tag tag-div">
    <h1>This is an Tag page</h1>
    <ContainerView @add-input-tag="addInputTag" />
    <ContainerTagView :tags="tags" />
  </div>
</template>

<script>
import { ref } from 'vue';
import ContainerView from "../../components/layouts/ContainerView.vue";
import ContainerTagView from "../../components/layouts/ContainerTagView.vue";

export default {
  name: "TagView",
  components: {
    ContainerView,
    ContainerTagView,
  },
  setup() {
    const tags = ref([]);

    const addInputTag = (inputTag) => {
      tags.value.push(inputTag);
    };

    return {
      tags,
      addInputTag,
    }
  }
};
</script>

<style lang="scss">
@import "../../assets/style/scss/tagView.scss";
</style>
