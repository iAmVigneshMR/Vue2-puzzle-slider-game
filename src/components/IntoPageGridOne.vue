<template>
  <div>
    <ImageSelector @gameStartTwo="gameStart" />
  </div>
</template>

<script>

import ImageSelector from './ImageSelector.vue';

export default {
  name: 'IntoPageGridOne',
  // props: {
  //   msg: String
  // },
  components: {
    ImageSelector,
    // IntoPageGridTwo
  },
  methods: {
    gameStart(val) {
      //console.log("child 1", val);
      // //console.log("suhdjgdhg");
      // //console.log({ val });
      this.$emit('gameStart', { ...val })
    },
  }
}
</script>