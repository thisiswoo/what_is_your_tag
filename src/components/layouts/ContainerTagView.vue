<template>
  <section class="container__tag">
    <article 
      class="tag"
      v-for="(t, index) in tags"
      :key="index"
      @click="clickTag"
      :style="{
        backgroundColor: `rgba(${t.tagColors[0]}, ${t.tagColors[1]}, ${t.tagColors[2]}, 0.7)`
      }" 
    >#{{ t.tagName }}</article>
  </section>
</template>

<script>
import { onMounted } from '@vue/runtime-core';
export default {
  props: {
    tags: {
      type: Array,
      required: true,
    }
  },
  setup(props, {emit}) {
    // let tagList = [];

    onMounted(() => {
      // tagList = [...props.tags]; // deep copy (spread 문법) 새로운 객체로 덮어씌우기
      // JSON.parse(JSON.stringify(props.tags));  // deep copy, JSON.stringify()로 문자열로 만든 다음 JSON.parse()로 parsing 하여 새로운 객채로 만든다.
      
      // tagList = 
    });


    // tag 클릭 후 부모 Component에 데이터 보내기.
    const clickTag = (e) => {
      // 태그 이름 꺼내어 부모 Component에 태그 이름만 보내주기.
      let selectedTagName = e.target.textContent;
      let resultTagName = selectedTagName.replace('#', '');
      emit('click-tag', {
        clickTagName: resultTagName,
      });
    };

    // let tagBackground = (index) => {
    //   return `background-color: rgba(
    //     ${props.tags[index].tagColors[0]}, 
    //     ${props.tags[index].tagColors[1]}, 
    //     ${props.tags[index].tagColors[2]}, 
    //     0.7);`
    // };

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