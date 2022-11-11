<template>
  <section class="container__tag">
    <article 
      class="tag"
      v-for="t in tags"
      :key="t.tagName"
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
  }
}
</script>

<style lang="scss">
@import "../../assets/style/scss/containerTagView.scss";
</style>