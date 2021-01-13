<template lang="pug">
.index
  Start(@upNumber="addNumber" v-if="startClicked === 0")
  Shindan(@upNumber="addNumber" v-for="(q, i) in quiz" v-if="startClicked === (i + 1)", :key="i", :question="q")
  Result(v-if="startClicked === 6")
</template>

<script>
import Start from '~/components/Start.vue'
import Shindan from '~/components/Shindan.vue'
import Result from '~/components/Result.vue'

export default {
  components:{
    Start,
    Shindan,
    Result
  },
  data() {
    return {
      startClicked: 0,
      quiz: [
        {
          text: "旅の予算は？",
          id: 1,
          questionList: [
            {
              n: "A",
              text: "5万円以下"
            },
            {
              n: "B",
              text: "5~15万円"
            },
            {
              n: "C",
              text: "15万円以上"
            }
          ]
        },
        {
          text: "いつ頃行きたい？",
          id: 2,
          questionList: [
            {
              n: "A",
              text: "春"
            },
            {
              n: "B",
              text: "夏"
            },
            {
              n: "C",
              text: "秋"
            },
            {
              n: "D",
              text: "冬"
            }
          ]
        },
        {
          text: "誰と行く？",
          id: 3,
          questionList: [
            {
              n: "A",
              text: "家族"
            },
            {
              n: "B",
              text: "友達"
            },
            {
              n: "C",
              text: "ひとり"
            }
          ]
        },
        {
          text: "一番重視することは？",
          id: 4,
          questionList: [
            {
              n: "A",
              text: "世界遺産"
            },
            {
              n: "B",
              text: "買い物"
            },
            {
              n: "C",
              text: "食事"
            },
            {
              n: "D",
              text: "街の景観"
            }
          ]
        },
        {
          text: "不安なことは？",
          id: 5,
          questionList: [
            {
              n: "A",
              text: "衛生面"
            },
            {
              n: "B",
              text: "治安"
            },
            {
              n: "C",
              text: "言語"
            }
          ]
        },
      ]
    }
  },
  methods: {
    addNumber(n) {
      return this.startClicked += n
    }
  }
}

</script>

<style lang="sass">
.index
  max-width: 375px
  height: 680px
  margin: 100px auto
  padding: 32px 20px
  text-align: center
  border: 5px solid #ffffff
  border-radius: 32px
</style>
