<template lang="pug">
.result__container
  h1.result__title 診断結果
  .result__content
    p.result__text
      |あなたにおすすめの国は
      br
      span.result__country 台湾
      br
      |です。
    .result-img
  .result__share
    p シェア
  button.index__button もう一度やる
</template>
<script>
</script>
<style lang="sass">
.result__text
  margin-top: 24px
  line-height: 1.5

.result__country
  font-size: 40px
  font-weight: bold

.result-img
  width: 200px
  height: 200px
  margin: 24px auto 0
  background-color: #333333

.result__share
  margin-top: 24px
</style>
