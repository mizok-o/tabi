<template lang="pug">
.q__container
  h1.q__title 第{{question.id}}問
  p.q__text {{ question.text }}
  .q__content
    ul.q__list
      QItem(v-for="(item, i) in question.questionList", :key="'q-' + i", :item="item")
  button(@click="shindanStart").index__button 次の問題へ
</template>

<script>
import QItem from '~/components/QItem.vue'
import Mixin from '~/plugins/mixin'

export default {
  props: {
    question: Object
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
