<template lang="pug">
.start__contaienr
  logo
  h1.start__title あなたの海外旅行診断
  p.start__sub 8つの質問であなたが訪れるべき国を診断します！次行く旅行の参考になるかも？？
  button(@click="shindanStart").index__button 診断開始
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

.start__title
  margin-top: 40px
  font-size: 32px

.start__sub
  margin-top: 24px
  font-size: 16px

.index__button
  width: 200px
  height: 48px
  margin-top: 80px
  font-weight: bold
  cursor: pointer
  border-radius: 24px
  border: none
  background-color: #ffffff

</style>
