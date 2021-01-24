<template lang="pug">
.index__container
  <!-- スタート画面 -->
  transition(name="fade" mode="out-in" @after-enter="afterEnter")
    .start__contaienr(v-if="startClicked === 0")
      h1.start__title
      p.start__sub 5つの質問であなたにおすすめの海外旅行の旅先を診断します！
      #foot
        img.start__footprint-img(
        v-for="(src, n) in urlList"
        :key="'sImg' + n"
        :class="'sImg-' + n"
        :src="src")
      button.index__button.start__button(@click="shindanStart") 診断開始
    <!-- 質問 -->
    .q__container(
      v-if="startClicked === (i + 1)"
      v-for="(q, i) in quizList"
      :class="'q__container-' + i"
      :key="i")
      .q__content
        h1.q__title 第{{q.id}}問
        p.q__text {{ q.text }}
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
      .result__content
        h1.result__title 診断結果
        p.result__maintext
          |あなたにおすすめの国は
          br
          span(:style="{ backgroundImage: 'url(' + result.country + ')' }").result__country
          |です。
        img.result-img(:src="result.img")
        p.result__subtext {{ result.text }}
        Share
      button(@click="reStart").index__button もう一度やる
</template>

<script>
import quizList from '../plugins/question'
import resultList from '../plugins/result'
import Share from '~/components/Share.vue'

export default {
  components:{
    Share
  },
  data() {
    return {
      startClicked: 0,
      urlList: [
        require("~/assets/img/footprint/foot01.svg"),
        require("~/assets/img/footprint/foot02.svg"),
        require("~/assets/img/footprint/foot03.svg"),
        require("~/assets/img/footprint/foot04.svg"),
        require("~/assets/img/footprint/foot05.svg"),
        require("~/assets/img/footprint/foot06.svg")
      ],
      quizList: quizList,
      answer: ["", "", "", ""],
      result: "",
      resultList: resultList
    }
  },
  mounted() {
    window.onload = () => {
      document.getElementById('foot').className = 'foot-appear'
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
      const fr = this.answer.reduce((x, y) => x + y.fr, 0)
      const neth = this.answer.reduce((x, y) => x + y.neth, 0)
      const itly = this.answer.reduce((x, y) => x + y.itly, 0)
      const eng = this.answer.reduce((x, y) => x + y.eng, 0)
      const egy = this.answer.reduce((x, y) => x + y.egy, 0)
      const anta = this.answer.reduce((x, y) => x + y.anta, 0)

      const resultArray = [viet, thai, thaiw, fr, neth, itly, eng, egy, anta];
      console.log(resultArray);

      const max = resultArray.reduce((a, b) => Math.max(a, b))
      console.log("max");
      console.log(max);

      let result = resultArray.filter(score => score === max);
      console.log("result");
      console.log(result);

      if (result.length > 1) {
        result = result[Math.floor(Math.random() * result.length)]
      }
        this.result = this.resultList[resultArray.indexOf(max)]
        console.log(this.result);
    },
    reStart() {
      return this.startClicked = 0
    },
    afterEnter() {
    }
  }
}

</script>

<style lang="sass">
.fade-enter-active
  animation: enter .5s cubic-bezier(0.5, 1, 0.89, 1)

@keyframes enter
  0%
    transform: translateX(64px)

  80%
    transform: translateX(0)

.index__container
  position: relative
  max-width: 375px
  padding: 48px 20px 24px
  text-align: center
  border: 3px solid $color-accent
  border-bottom: none
  border-top: none
  @media screen and (max-width: 375px)
    border: none

/* スタート */

.start__contaienr
  width: 100%
  height: 100%
  text-align: center

.start__title
  height: 32px
  background-size: auto
  background-repeat: no-repeat
  background-image: url('~assets/img/top-title.svg')

.start__sub
  margin-top: 32px
  text-align: center
  font-size: 18px
  font-weight: bold

.foot-appear
  width: 100%
  height: 232px

.start__footprint-img
  position: absolute
  width: 54px
  height: 32px
  opacity: 0
  transition: opacity .3s cubic-bezier(0.5, 0, 0.75, 0)

.foot-appear
  .start__footprint-img
    opacity: 1

.sImg-0
  bottom: 202px
  left: 0
  transition-delay: .5s

.sImg-1
  bottom: 178px
  left: 67px
  transition-delay: .9s

.sImg-2
  bottom: 207px
  left: 128px
  transition-delay: 1.1s

.sImg-3
  bottom: 191px
  left: 200px
  transition-delay: 1.4s

.sImg-4
  bottom: 238px
  left: 256px
  transition-delay: 1.6s

.sImg-5
  bottom: 235px
  left: 317px
  transition-delay: 2s
  @media screen and (max-width: 375px)
    left: 322px

.index__button
  width: 200px
  height: 48px
  margin-top: 96px
  font-weight: bold
  color: $color-main
  cursor: pointer
  border-radius: 24px
  border: none
  border: 1px solid $color-main

.start__button
  margin-top: 96px


/* 診断1問目〜5問 */

.q__container
  display: flex
  width: 100%
  height: 100%
  padding-bottom: 24px
  flex-direction: column
  justify-content: space-between
  align-items: center

.q__text
  margin-top: 24px
  font-size: 20px
  font-weight: bold

.q__list
  margin: 32px 0 0

.q__list__item
  position: relative
  display: flex
  width: 320px
  height: 56px
  justify-content: center
  align-items: center
  margin: 24px auto 0
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

.result__container
  display: flex
  height: 650px
  flex-direction: column
  justify-content: space-between
  align-items: center
  .index__button
    margin-top: 32px

.result__title
  font-weight: bold

.result__maintext
  margin-top: 8px
  span
    display: block
    width: 162px
    height: 40px
    margin: 8px auto
    background-size: contain
    background-repeat: no-repeat

.result-img
  width: 160px
  height: 160px
  margin: 24px auto 0

.result__subtext
  margin-top: 16px
  font-size: 16px
  text-align: left

</style>
