<template lang="pug">
.index__container
  <!-- スタート画面 -->
  .start__contaienr(v-if="startClicked === 0")
    logo
    h1.start__title みんなの旅先診断
    p.start__sub 5つの質問であなたにおすすめの旅先（海外旅行）を診断します！
    button(@click="shindanStart").index__button 診断開始
  <!-- 質問 -->
  .q__container(v-if="startClicked === (i + 1)" v-for="(q, i) in quizList", :key="i")
    h1.q__title 第{{q.id}}問
    p.q__text {{ q.text }}
    .q__content
      ul.q__list
        li.q__list__item(v-for="(item, index) in q.questionList", :key="'q-' + item.n")
          input.q__list__item-radio(
            type="radio"
            :name="'que-' + q.id"
            :value="item.sArea"
            v-model="answer[i]")
          p.q__list__item-text {{ item.text }}
    button(@click="toResult" v-if="startClicked === 5", :disabled="!answer[i]").index__button 診断結果を見る
    button(@click="shindanStart" v-else :disabled="!answer[i]").index__button 次の問題へ
  <!-- 結果 -->
  .result__container(v-if="startClicked === 6")
    h1.result__title 診断結果
    .result__content
      p.result__maintext
        |あなたにおすすめの国は
        br
        span.result__country {{ result.country }}
        br
        |です。
      p.result__subtext {{ result.text }}
      img.result-img(:src="result.url")
    Share
    button(@click="reStart").index__button もう一度やる
</template>

<script>
import Logo from '~/components/Logo.vue'
import quizList from '../plugins/question'
import resultList from '../plugins/result'
import Share from '~/components/Share.vue'

export default {
  components:{
    Logo,
    Share
  },
  data() {
    return {
      startClicked: 0,
      quizList: quizList,
      answer: ["", "", "", ""],
      result: "",
      resultList: resultList
    }
  },
  methods: {
    shindanStart() {
      return this.startClicked += 1
    },
    toResult() {
      this.startClicked = 6
      console.log(this.answer);

      const viet = this.answer.reduce((x, y) => x + y.viet, 0)
      const thai = this.answer.reduce((x, y) => x + y.thai, 0)
      const thaiw = this.answer.reduce((x, y) => x + y.thaiw, 0)
      const resultArray = [viet, thai, thaiw];
      console.log(resultArray);
      const max = resultArray.reduce((a, b) => Math.max(a, b))
      console.log("max");
      console.log(max);
      const result = resultArray.filter(score => score === max);
      console.log("result");
      console.log(result);
      console.log(this.resultList);
      this.result = this.resultList[resultArray.indexOf(max)]
      console.log(this.result);

    },
    reStart() {
      return this.startClicked = 0
    }
  }
}

</script>

<style lang="sass">
.index__container
  max-width: 375px
  max-height: 800px
  height: 100vh
  margin: auto
  padding: 24px 20px
  text-align: center
  border: 5px solid $color-main

/* スタート */

.start__contaienr
  text-align: center

.start__title
  margin-top: 40px
  font-family: $font-title
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
  color: $color-letter
  cursor: pointer
  border-radius: 24px
  border: none
  border: 1px solid $color-main

/* 診断1問目〜5問 */

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
  border: 1px solid $color-main

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

.index__button[disabled]
  opacity: .2
  pointer-events: none

/* 結果 */

.result__title
  font-size: 32px

.result__maintext
  margin-top: 32px

.result__subtext
  margin-top: 12px
  font-size: 16px

.result__country
  font-family: $font-title
  font-size: 40px

.result-img
  width: 160px
  height: 160px
  margin: 32px auto 0

</style>
