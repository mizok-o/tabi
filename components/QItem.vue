<template lang="pug">
li.q__list__item
  input.q__list__item-radio(type="radio")
  p.q__list__item-text {{ item.text }}
</template>
<script>
export default {
  props: {
    item: Object
  }
}
</script>
<style lang="sass">

</style>
