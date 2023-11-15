<script setup>
defineProps({
  or: {
    type: Number,
    required: true
  },
  troupes: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <aside class="solde-or">
    <div>
      <img src="/img/piece-or-note.jpg" alt="Solde Or">
      {{ or.toLocaleString('fr-CH') }} pièces d'or
    </div>
    <div>
      <img src="/img/troupes-icon.png" alt="Troupes">
      {{ troupes.length }} troupes formées
    </div>
  </aside>
</template>

<style scoped lang="sass">
aside
  position: fixed
  width: 100%
  background: white
  color: #3B3B3B
  font-size: 1.25rem
  padding: .5rem
  z-index: 9999
  box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px
  display: flex
  justify-content: space-between
  flex-wrap: wrap
  gap: 1em

  img
    max-height: 3rem
    vertical-align: middle
</style>