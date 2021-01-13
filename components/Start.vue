<template lang="pug">
.start__contaienr
  logo
  h1.start__title 旅先診断
  p.start__sub 5つの質問であなたにおすすめの旅先（海外旅行）を診断します！
  button(@click="shindanStart").index__button 診断開始
</template>

<script>
import Logo from '~/components/Logo.vue'
import Mixin from '~/plugins/mixin'

export default {
  components:{
    Logo
  },
  mixins: [Mixin]
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
  font-size: 18px

.index__button
  position: absolute
  bottom: 48px
  left: 50%
  transform: translateX(-50%)
  width: 200px
  height: 48px
  font-weight: bold
  cursor: pointer
  border-radius: 24px
  border: none
  background-color: #ffffff

</style>
