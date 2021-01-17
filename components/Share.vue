<template lang="pug">
.result__share
  p シェア
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
</template>
<style lang="sass">
  .result__share
    font-weight: bold
    margin-top: 56px

  .result__share__container
    display: flex
    width: 96px
    justify-content: space-between
    margin: 12px auto 0

  .result__share__item-link

  .share-twitter
    &::before
      content: ""
      display: block
      width: 28px
      height: 28px
      margin-top: 2px
      background-repeat: no-repeat
      background-size: contain
      background-image: url('~assets/img/twitter.svg')

  .share-line
    &::before
      content: ""
      display: block
      width: 28px
      height: 28px
      background-repeat: no-repeat
      background-size: contain
      background-image: url('~assets/img/LINE.svg')
</style>
