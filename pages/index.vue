<template lang="pug">
.index
  Start(@upNumber="addNumber" v-if="startClicked === 0")
  Shindan(v-for="(item, i) in quizList" v-if="startClicked === 1", :key="i")
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
        {title: "あなたの好きな食べ物は", id: 1}
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

</style>
