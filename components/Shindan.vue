<template lang="pug">
.q__container
  h1.q__title 第{{qChild.id}}問
  p.q__text {{ qChild.text }}
  .q__content
    ul.q__list
      QItem(
        v-for="(item, index) in qChild.questionList", :key="'q-' + index"
        :item="item"
        :qGrand="qChild"
        v-model="answer")
  button(@click="toResult" v-if="buttonN === 5").index__button 診断結果を見る
  button(@click="toNext" v-else).index__button 次の問題へ

</template>

<script>
import QItem from '~/components/QItem.vue'

export default {
  props: {
    qChild: Object,
    buttonN: Number
  },
  components: {
    QItem
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

</style>
