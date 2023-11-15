<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {ref, onMounted} from 'vue'
import PageFooter from "@/components/PageFooter.vue";
import PageTopBar from "@/components/PageTopBar.vue";
import TroupeCarte from "@/components/TroupeCarte.vue";
import PageHeader from "@/components/PageHeader.vue";

// Tableau des troupes
const troupes = ref([])

// Tableau des troupes formées
const troupesFormees = ref([])

// Total d'or
const totalOr = ref(20000)

// Cycle de vie du composant
// Quand le composant est monté, on va chercher les données
onMounted(() => {
  fetch('https://cocapi.divtec.me/troupes')
      .then((res) => res.json()) // Transforme le json en JavaScript
      .then((data) => { // Récupère les données et les sauve dans le tableau
        troupes.value = data
      })
})


/* Méthodes */
function formerTroupe(troupe) {
  if (totalOr.value < troupe.cout) {
    alert("Vous n'avez pas assez d'or mon seigneur !")
    return
  }
  totalOr.value -= troupe.cout
  troupesFormees.value.push(troupe)
}
</script>

<template>
  <page-top-bar :or="totalOr" :troupes="troupesFormees"/>

  <page-header/>

  <main>
    <ul class="cartes">
      <li
          v-for="troupe in troupes"
          :key="troupe.id"
      >
        <troupe-carte
            :troupe="troupe"
            :or="totalOr"
            @former="formerTroupe"
        />
      </li>
    </ul>
  </main>

  <page-footer/>

</template>

<style scoped lang="sass">
/* https://sass-lang.com/guide */

</style>