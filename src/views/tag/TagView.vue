<template>
  <div 
    class="tag-div"
    :style="responseURL"
  >
    <section class="container">
      <ContainerView 
        @add-input-tag="addInputTag" 
      />
      <ContainerTagView 
        :tags="tags"
        @click-tag="clickTag"
      />
    </section>
  </div>
</template>

<script>
import { ref } from 'vue';
import ContainerView from "../../components/layouts/ContainerView.vue";
import ContainerTagView from "../../components/layouts/ContainerTagView.vue";
import axios from 'axios';

export default {
  name: "TagView",
  components: {
    ContainerView,
    ContainerTagView,
  },
  setup() {
    const tags = ref([]);
    const responseURL = ref('');

    // input에 입력시 추가되는 태그.
    const addInputTag = async (result) => {
      tags.value.push(result);

      try {
        const res = await axios.get(`https://source.unsplash.com/featured/?${result.tagName.toLowerCase()}`);
        responseURL.value = "background-image:url(" + res.request.responseURL + ")";
      } catch(error) {
        console.log('addInputTag async error : ', error);
      }
    };

    // 추가된 태그를 클릭하였을때 해당 태그의 이름으로 배경 바꾸기.
    const clickTag = async (result) => {
      try {
        const res = await axios.get(`https://source.unsplash.com/featured/?${result.clickTagName.toLowerCase()}`);
        responseURL.value = "background-image:url(" + res.request.responseURL + ")";
      } catch(error) {
        console.log('clickTag async error : ', error);
      }
    };

    return {
      tags,
      addInputTag,
      responseURL,
      clickTag,
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
