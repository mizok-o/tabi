<template lang="pug">
li.q__list__item
  input.q__list__item-radio(
    type="radio"
    :name="'q-' + qGrand.id"
    :value="value"
    @input="$emit('input', item.sArea)")
  p.q__list__item-text {{ item.text }}
</template>
<script>
export default {
  props: {
    qGrand: Object,
    item: Object,
    value: {
      type: ''
    }
  }
}
</script>
<style lang="sass">
.q__list__item
  position: relative
  display: flex
  width: 320px
  height: 56px
  justify-content: center
  align-items: center
  margin-top: 24px
  border-radius: 28px
  background-color: $color-base

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
</style>
