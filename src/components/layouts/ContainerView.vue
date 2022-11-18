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
    const tagColors = ref([]);

    // 태그 입력 후 enter를 눌렀을때 부모로 값 보내주기.
    const enterTag = () => {
      if (inputTag.value !== '') {
        emit('add-input-tag', {
          tagName: inputTag.value,
          tagColors: getRandomRGB(180, 230)
        });
        inputTag.value = '';
      }
    };

    // 태그 랜덤값 보내주기
    const randomRGB = (min, max) => {
      return Math.floor(Math.random() * (max - min) + 1) + min;
    }
    const getRandomRGB = (min, max) => {
      let arrRGB = [];
      arrRGB.push(randomRGB(min, max));
      arrRGB.push(randomRGB(min, max));
      arrRGB.push(randomRGB(min, max));
      return arrRGB;
    }
    
    return {
      inputTag,
      enterTag,
      tagColors,
    }
  }
};
</script>

<style lang="scss">
@import "../../assets/style/scss/containerView.scss";
</style>
