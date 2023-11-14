<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {ref} from 'vue'

// Tableau des troupes
const troupes = ref([
  {
    "id": 2,
    "nom": "Archer",
    "niveau": 3,
    "formation": 25,
    "vitesse": 24,
    "cout": 200,
    "description": "Les archers sont des tireurs d'élite qui attaquent à distance. Ils sont rapides et bon marché à former, mais ils sont faibles en mêlée et doivent être protégés.",
    "couleur": "#EE5487",
    "image": "https://cocapi.divtec.me/img/archer.png"
  },
  {
    "id": 1,
    "nom": "Barbare",
    "niveau": 4,
    "formation": 20,
    "vitesse": 16,
    "cout": 150,
    "description": "Ce guerrier intrépide compte sur ses muscles saillants et sa fière moustache pour semer le chaos dans les villages ennemis. Faites charger une horde de barbares et profitez du spectacle !",
    "couleur": "#ebb428",
    "image": "https://cocapi.divtec.me/img/barbare.png"
  },
  {
    "id": 3,
    "nom": "Géant",
    "niveau": 5,
    "formation": 12,
    "vitesse": 12,
    "cout": 2250,
    "description": "Les géants sont de grands guerriers qui attaquent les défenses ennemies en premier. Ils sont lents mais résistants.",
    "couleur": "#F6901A",
    "image": "https://cocapi.divtec.me/img/geant.png"
  }
])
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
              :style="`color: ${troupe.couleur};`">
            Niveau {{ troupe.niveau }}
          </div>
          <h2 class="name">{{ troupe.nom }}</h2>
          <button
              :style="`background-color: ${troupe.couleur};`"
          > Former
            <img src="/img/piece-or.png" alt="Former"></button>
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

  <footer>
    &copy; 2023 - Supercell.com
  </footer>
</template>

<style scoped lang="sass">
/* https://sass-lang.com/guide */

</style>