<template lang="pug">
.index__container
  Start(@upNumber="addNumber" v-if="startClicked === 0")
  Shindan(
    @upNumber="addNumber"
    v-if="startClicked === (i + 1)"
    v-for="(q, i) in quizL", :key="i"
    :qChild="q",
    :buttonN="startClicked")
  Result(v-if="startClicked === 6" @setZero="reset")
</template>

<script>
import Start from '~/components/Start.vue'
import Shindan from '~/components/Shindan.vue'
import Result from '~/components/Result.vue'
import quizList from '../plugins/data'

export default {
  components:{
    Start,
    Shindan,
    Result
  },
  data() {
    return {
      startClicked: 0,
      quizL: quizList
    }
  },
  methods: {
    addNumber(n) {
      return this.startClicked += n
    },
    reset(s) {
      return this.startClicked = s
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
  padding: 32px 20px
  text-align: center
  background-color: #222222
</style>
