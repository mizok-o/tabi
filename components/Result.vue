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
    .result__share__title シェア
    ul.result__share__container
      li.result__share__item
        - url = 'https://wataridori.netlify.app'
        - text = 'みたらし'
        - hashtags = '診断アプリ'
        a.result__share__item-link.share-twitter(
          href=`https://twitter.com/share?url=${url}&text=${text}&hashtags=${hashtags}`
          target="_blank"
          rel="noopener")
      li.result__share__item
        a.result__share__item-link.share-line(
          href=`https://social-plugins.line.me/lineit/share?url=${url}`
          target="_blank"
          rel="noopener")
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
  width: 160px
  height: 160px
  margin: 24px auto 0
  background-color: #333333

.result__share
  margin-top: 24px

.result__share__container
  display: flex
  width: 120px
  justify-content: space-between
  margin: 12px auto 0

.result__share__item-link

.share-twitter
  &::before
    content: ""
    display: block
    width: 48px
    height: 48px
    margin-top: 5px
    background-repeat: no-repeat
    background-size: contain
    background-image: url('~assets/img/twitter.svg')

.share-line
  &::before
    content: ""
    display: block
    width: 48px
    height: 48px
    background-repeat: no-repeat
    background-size: contain
    background-image: url('~assets/img/LINE.svg')

</style>
