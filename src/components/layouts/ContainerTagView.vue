<template>
  <section class="container__tag">
    <article 
      class="tag"
      v-for="(t, index) in tags"
      :key="index"
      @click="clickTag"
    >#{{ t.tagName }}</article>
  </section>
</template>

<script>
// import { watch } from 'vue';

export default {
  props: {
    tags: {
      type: Array,
      required: true,
    }
  },
  setup(props, {emit}) {
    // const tagBackground = ref('');

    console.log('props tags : ', props.tags);
    // let test = ref(props.tags);

    const clickTag = (e) => {
      // 태그 이름 꺼내어 부모 Component에 태그 이름만 보내주기.
      let selectedTagName = e.target.textContent;
      let resultTagName = selectedTagName.replace('#', '');
      emit('click-tag', {
        clickTagName: resultTagName,
        });
    };

    // watch((tagBackground), (current, prev) => {
      //   console.log('watch : ', current, prev);
    //   tagBackground.value = `background-color: rgba(${result.tagColors[0]}, ${result.tagColors[1]}, ${result.tagColors[2]}, 0.7);`
    // });
    
    // watch((props.tags), (current, prev) => {
    //   console.log('watch : ', current, prev);
    //   console.log('props tags : ', props.tags.tagColors);
    //   // tagBackground.value = `background-color: rgba(${result.tagColors[0]}, ${result.tagColors[1]}, ${result.tagColors[2]}, 0.7);`
    // });

    return {
      clickTag,
    }
  }
}
</script>

<style lang="scss">
@import "../../assets/style/scss/containerTagView.scss";
</style>