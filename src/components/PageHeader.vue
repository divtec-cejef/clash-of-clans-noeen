<script setup>

</script>

<template>
  <header>
    <h1>
      <img src="/img/clash-of-clans-logo.webp" alt="Logo Clash of Clans">
    </h1>
    <p class="description">
      Construire un village,
      former un clan et participer à des guerres de clans épiques !
    </p>
  </header>
</template>

<style scoped lang="sass">
header
  padding: 80px 0 20px
  text-align: center

  h1 img
    max-height: 150px

  h1,
  .description
    font-size: 3.25rem
    color: white
    text-shadow: 1px 1px 2px black /* offset-x | offset-y | blur-radius | color */

  h1
    margin: 0

  .description
    font-size: 1.5rem
    line-height: 1.25
    max-width: 640px
    margin: 0 auto 1em
</style>