<template lang="pug">
.q__container
  h1.q__title 第{{qChild.id}}問
  p.q__text {{ qChild.text }}
  .q__content
    ul.q__list
      li.q__list__item(
        v-for="(item, index) in qChild.questionList", :key="'q-' + index"
        :item="item"
        v-model="answer")
        input.q__list__item-radio(
          type="radio"
          :name="'q-' + item.id"
          :value="value"
          @input="$emit('input', item.sArea)")
        p.q__list__item-text {{ item.text }}
  button(@click="toResult" v-if="buttonN === 5").index__button 診断結果を見る
  button(@click="toNext" v-else).index__button 次の問題へ

</template>

<script>
export default {
  props: {
    qChild: Object,
    buttonN: Number,
    value: {
      type: ''
    }
  },
  data() {
    return {
      answer: [],
      eu: "",
      as: "",
      us: "",
      A: [],
    }
  },
  computed: {
    asia() {
      this.as = this.answer.as
      this.A.push(this.as)
      return this.A.reduce((a, b) => a + b)
    }
  },
  methods: {
    toResult() {
      this.$emit('upNumber', 1);
    },
    toNext() {
      this.$emit('upNumber', 1);
    }
  }
}
</script>

<style lang="sass">
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
  background-color: $color-base

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
  color: $color-main
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
    background-size: contain
    background-repeat: no-repeat
    background-image: url('~assets/img/check.svg')
</style>
