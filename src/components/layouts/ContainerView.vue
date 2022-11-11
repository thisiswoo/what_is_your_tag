<template>
  <input
      type="text"
      class="addTag"
      placeholder="what is your tag?"
      spellcheck="false"
      v-model="inputTag"
      @keyup.enter="enterTag"
    />
</template>

<script>
import { ref } from 'vue';

export default {
  emits: ['add-input-tag'],

  setup(props, {emit}) {
    const inputTag = ref('');

    const enterTag = () => {
      console.log('emit ------> : ', inputTag.value);
      if (inputTag.value !== '') {
        emit('add-input-tag', {
          tagName: inputTag.value,
        });
        inputTag.value = '';
      }
    };
    
    return {
      inputTag,
      enterTag,
    }
  }
};
</script>

<style lang="scss">
@import "../../assets/style/scss/containerView.scss";
</style>
