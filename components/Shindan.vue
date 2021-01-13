<template lang="pug">
.q__container
  h1.q__title 第{{qChild.id}}問
  p.q__text {{ qChild.text }}
  .q__content
    ul.q__list
      QItem(
        v-for="(item, i) in qChild.questionList", :key="'q-' + i"
        :item="item"
        :qGrand="qChild")
  button(@click="shindanStart" v-if="buttonN < 5").index__button 次の問題へ
  button(@click="shindanStart" v-else).index__button 診断結果を見る
</template>

<script>
import QItem from '~/components/QItem.vue'
import Mixin from '~/plugins/mixin'

export default {
  props: {
    qChild: Object,
    buttonN: Number
  },
  components:{
    QItem
  },
  mixins: [Mixin]
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
