<template lang="pug">
.start__contaienr
  logo
  h1 あなたにおすすめな旅先を診断します
  button(@click="shindanStart").index__start-button 診断開始
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components:{
    Logo
  },
  methods: {
    shindanStart() {
      this.$emit('upNumber', 1);
    }
  }
}

</script>

<style lang="sass">
.start__contaienr
  text-align: center
.index__start-button

</style>
