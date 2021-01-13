<template lang="pug">
.q__container
  h1.q__title 第一問
  p.q__text あなたの好きな食べ物は？
  .q__content
    ul.q__list
      QItem(v-for="(item, i) in questionList", :key="i", :item="item")
  button(@click="shindanStart").index__button 次の問題へ
</template>

<script>
import QItem from '~/components/QItem.vue'

export default {
  data() {
    return {
      questionList: [
        { n: "A", text: "ラーメン" },
        { n: "B", text: "牛丼" },
        { n: "C", text: "ハンバーガー" }
      ]
    }
  },
  components:{
    QItem
  },
  methods: {
    shindanStart() {
      this.$emit('upNumber', 1);
    }
  }
}
</script>

<style lang="sass">
.q__container
  text-align: center

.q__text
  margin-top: 24px
  font-size: 20px
  font-weight: bold

.q__content
  margin: 64px 0 0

.q__list__item
  position: relative
  display: flex
  width: 320px
  height: 56px
  justify-content: center
  align-items: center
  margin-top: 24px
  border-radius: 28px
  background-color: #ffffff

.q__list__item-radio
  position: absolute
  top: 0
  left: 0
  width: 100%
  height: 100%
  opacity: 0
  cursor: pointer
  &:checked + .q__list__item-text
    &::before
      opacity: 1

.q__list__item-text
  color: #111
  font-weight: bold
  &::before
    content: ""
    position: absolute
    top: 50%
    left: 16px
    transform: translateY(-50%)
    display: block
    width: 24px
    height: 24px
    opacity: 0
    border: 1px solid #111111
    border-radius: 50%

</style>
