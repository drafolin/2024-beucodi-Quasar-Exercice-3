<template>
<!--
Exercice 3 - Pinia & Formulaires

1) Créer un magasin Pinia avec le nom "plat" pour les plats
   dans src/store/ et y ajouter le tableau des plats.

2) Afficher les plats sur la page Exercice.vue à l'aide du useStore

3) Ajouter la possibilité de supprimer un élément (clic sur bouton supprimer)
   en utilisant des actions et des mutations.
   Afficher une dialog de confirmation avant de supprimer.

4) Ajouter une validation au formulaire src/components/FormPlat.vue
     - nom: obligatoire avec un maximum de 20 caractères.
     - description: maximum de 155 caractères.
     - La validation doit être déclenchée lorsque l'on clique sur Sauvegarder

5) Ajouter la possibilité d'ajouter un élément
   indice: utiliser l'attribut "action" pour différencier l'ajout de la modification

6) Ajouter la possibilité de modifier un élément

7) Si aucune description n'est fournie pour un plat,
   afficher le texte "Aucune description fournie" en italique

-->
<q-page class="q-pa-lg">
  <div class="row q-gutter-lg">

    <PlatComponent
      v-for="plat in plats"
      :key="plat.id"
      :plat="plat" />

    <bouton-ajouter
      @click="afficherFormPlat = true" />

    <q-dialog
      v-model="afficherFormPlat">
      <form-plat action="ajouter" />
    </q-dialog>

  </div>
</q-page>
</template>

<script setup>
import { ref } from 'vue'
import PlatComponent from 'components/PlatComponent.vue'
import BoutonAjouter from 'components/BoutonAjouter.vue'
import FormPlat from 'components/FormPlat.vue'

const plats = ref([
  {
    id: 1,
    image: 'https://i.imgur.com/0umadnY.jpg',
    nom: 'Burger',
    description: "Un hamburger est un sandwich composé d'une ou plusieurs tranches de viande hachée, généralement du bœuf, placées dans un petit pain ou une brioche.",
    note: 4
  },
  {
    id: 2,
    image: 'https://i.imgur.com/b9zDbyb.jpg',
    nom: 'Pizza',
    description: "La pizza est un plat savoureux d'origine italienne, consistant en une base généralement ronde et aplatie de pâte levée à base de blé.",
    note: 5
  },
  {
    id: 3,
    image: 'https://i.imgur.com/RbKjUjB.jpg',
    nom: 'Petits choux',
    description:
        'Le chou de Bruxelles est une variété de chou, plante herbacée de la famille des Brassicaceae. C’est vraiement pas bon...',
    note: 1
  },
  {
    id: 4,
    image: 'https://i.imgur.com/xAuhNVg.jpg',
    nom: 'BBQ Ribs',
    description: 'Les BBQ ribs ou barbecue ribs sont des grands classiques très appréciés partout dans le monde.',
    note: 5
  }
])

const afficherFormPlat = ref(false)
</script>
