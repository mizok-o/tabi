<template lang="pug">
.index
  Start(@upNumber="addNumber" v-if="startClicked === 0")
  Shindan(@upNumber="addNumber" v-for="(q, i) in quizList" v-if="startClicked === (i + 1)", :key="i", :question="q")
</template>

<script>
import Start from '~/components/Start.vue'
import Shindan from '~/components/Shindan.vue'

export default {
  components:{
    Start,
    Shindan
  },
  data() {
    return {
      startClicked: 0,
      quizList: [
        {text: "あなたの好きな食べ物は", id: 1},
        {text: "映画は", id: 2},
        {text: "あなたの好きな漫画は", id: 3}
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
  border: 5px solid #ffffff
  border-radius: 32px
</style>
