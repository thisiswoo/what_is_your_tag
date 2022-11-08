<template>
  <section class="container__tag">
    <div 
      v-for="t in tags"
      :key="t.tagName"
    >#{{ t.tagName }}</div>
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

<style>
@import "../../assets/style/scss/containerTagView.scss";
</style>