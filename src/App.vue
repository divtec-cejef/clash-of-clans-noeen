<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {ref, onMounted} from 'vue'
import PageFooter from "@/components/PageFooter.vue";

// Tableau des troupes
const troupes = ref([])

// Cycle de vie du composant
// Quand le composant est monté, on va chercher les données
onMounted(() => {
  fetch('https://cocapi.divtec.me/troupes')
      .then((res) => res.json()) // Transforme le json en JavaScript
      .then((data) => { // Récupère les données et les sauve dans le tableau
        troupes.value = data
      })
})
</script>

<template>
  <aside class="solde-or">
    <div>
      <img src="/img/piece-or-note.jpg" alt="Solde Or">
      20 000 pièces d'or
    </div>
    <div>
      <img src="/img/troupes-icon.png" alt="Troupes">
      0 troupes formées
    </div>
  </aside>

  <header>
    <h1>
      <img src="/img/clash-of-clans-logo.webp" alt="Logo Clash of Clans">
    </h1>
    <p class="description">
      Construire un village,
      former un clan et participer à des guerres de clans épiques !
    </p>
  </header>

  <main>
    <ul class="cartes">
      <li
          v-for="troupe in troupes"
          :key="troupe.id"
      >
        <article>
          <header
              :style="`background: linear-gradient(60deg,#3B3B3B 0%, ${troupe.couleur} 100%);`"
          >
            <img
                :src="troupe.image"
                :alt="troupe.nom"
            >
          </header>
          <div
              class="level"
              :style="`color: ${troupe.couleur};`"
          >
            Niveau {{ troupe.niveau }}
          </div>
          <h2 class="name">{{ troupe.nom }}</h2>
          <button
              :style="`background-color: ${troupe.couleur};`"
          > Former
            <img src="/img/piece-or.png" alt="Former">
          </button>
          <p class="description">{{ troupe.description }}</p>
          <footer>
            <div
                class="training"
                :style="`background-color: ${troupe.couleur};`"
            >
              <div>{{ troupe.formation }}<sup>sec</sup></div>
              <div>Formation</div>
            </div>
            <div
                class="speed"
                :style="`background-color: ${troupe.couleur};`"
            >
              <div>{{ troupe.vitesse }}</div>
              <div>Vitesse</div>
            </div>
            <div
                class="cost"
                :style="`background-color: ${troupe.couleur};`"
            >
              <div>{{ troupe.cout }}</div>
              <div>Coût</div>
            </div>
          </footer>
        </article>
      </li>
    </ul>
  </main>

  <page-footer />
</template>

<style scoped lang="sass">
/* https://sass-lang.com/guide */

</style>