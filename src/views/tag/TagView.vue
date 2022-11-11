<template>
  <div class="tag-div">
    <section class="container">
      <ContainerView @add-input-tag="addInputTag" />
      <ContainerTagView :tags="tags" />
    </section>
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

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
