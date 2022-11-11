<template>
  <div 
    class="tag-div"
    :style="responseURL"
  >
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
import axios from 'axios';

export default {
  name: "TagView",
  components: {
    ContainerView,
    ContainerTagView,
  },
  setup() {
    const tags = ref([]);
    let responseURL = ref('');

    const addInputTag = async (inputTag) => {
      console.log('parents inputTag : ', inputTag.tagName.toLowerCase());
      tags.value.push(inputTag);
      
      try {
        const res = await axios.get(`https://source.unsplash.com/featured/?${inputTag.tagName.toLowerCase()}`);
        responseURL.value = "background-image:url(" + res.request.responseURL + ")";
        console.log("responseURL >>", responseURL);
        console.log("responseURL value >>", responseURL.value);
        console.log('async res : ', res.request.responseURL);
      } catch(error) {
        console.log('async error : ', error);
      }
    };

    return {
      tags,
      addInputTag,
      responseURL,
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
