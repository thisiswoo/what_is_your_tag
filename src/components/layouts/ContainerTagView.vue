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
export default {
  props: {
    tags: {
      type: Array,
      required: true,
    }
  },
  setup(props, {emit}) {
    const clickTag = (e) => {
      let selectedTagName = e.target.textContent;
      let resultTagName = selectedTagName.replace('#', '');
      console.log('selectedTagName : ', selectedTagName);
      console.log('resultTagName : ', resultTagName);
      console.log('click tag : ', e.target.textContent);
      emit('click-tag', {
          clickTagName: resultTagName,
        });
    };

    return {
      clickTag,
    }
  }
}
</script>

<style lang="scss">
@import "../../assets/style/scss/containerTagView.scss";
</style>