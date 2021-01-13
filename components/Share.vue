<template lang="pug">
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
</template>
<style lang="sass">
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
