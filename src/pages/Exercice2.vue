<template>
  <!--
    Exercice 2 - Listes et composants Vue.js

    1) Créez un tableau pour les plats,  que vous voyez sur la page.
       Chaque objet du tableau doit contenir les propriété suivantes
       image (url de l’image), nom, description et note (note de 1 à 5)

    2) Créer une boucle v-for qui affiche ces aliments sur la page,
       avec toutes les données provenant du tableau des aliments
       (indice : pour l’image, à la place de l'attribut src,
       utiliser la directive :src)

    3) Ajoutez un de vos plats préférés à la liste
       Vous pouvez trouver des images ici : https://imgur.com/

    4) Créez un composant enfant pour les plats(components/Plat.vue)
       et utilisez-le pour afficher chacun de vos plats

    5) Dans le tableau des plats, ajoutez un identifiant unique (id)
       à chaque plats.
       Appliquez l'id à une propriété :key de votre boucle v-for.

    6) Ajouter un lien ou un bouton supprimer à votre composant enfant Plat,
       qui émettra un événement "supprimer" et passera l'id du plat.

    7) Dans la page, écouter l'événement "supprimer" et supprimer le plat
       du tableau des plats.

  -->
  <q-page padding>
    <div class="q-pa-md row items-stretch">
      <plat v-for="plat in plats" :key="plat.id" :plat="plat" v-on:suppPlat="deletePlat"></plat>
    </div>
  </q-page>
</template>

<script>
export default {
  components: {
    plat: require('components/Plats.vue').default
  },
  name: 'Exercice2',
  mounted () {
    document.title = 'Exercice 2 | Quasar'
  },
  methods: {
    deletePlat (id) {
      this.plats = this.plats.filter(function (plat) {
        return plat.id !== id
      })
    }
  },
  data () {
    return {
      plats: [
        {
          id: 1,
          nom: 'Hamburger',
          description: 'Un hamburger est un sandwich composé d\'une ou plusieurs tranches de ' +
            'viande hachée, généralement du bœuf, placées dans un petit pain ou une brioche.',
          image: {
            source: 'https://i.imgur.com/0umadnY.jpg',
            alt: 'Photo de Hamburger'
          },
          note: '4/5'
        },
        {
          id: 2,
          nom: 'Pizza',
          description: 'La pizza est un plat savoureux d\'origine italienne, consistant' +
            '            en une base généralement ronde et aplatie de' +
            '            pâte levée à base de blé.',
          image: {
            source: 'https://i.imgur.com/b9zDbyb.jpg',
            alt: 'Photo de Pizza'
          },
          note: '5/5'
        },
        {
          id: 3,
          nom: 'Petits choux',
          description: 'Le chou de Bruxelles est une variété de chou, plante herbacée de la famille des Brassicaceae.' +
            ' C’est vraiement pas bon...',
          image: {
            source: 'https://i.imgur.com/RbKjUjB.jpg',
            alt: 'Photo de petits choux'
          },
          note: '1/5'
        },
        {
          id: 4,
          nom: 'Lasagne',
          description: 'Les lasagne est un plat italien fait de couches alternées de pâtes, de' +
            ' fromage et d\'une sauce tomate avec de la viande.',
          image: {
            source: 'https://i.imgur.com/qxJvf3T.jpg',
            alt: 'Photo de lasagne à la bolognese'
          },
          note: '5/5'
        }

        // Vos objets plats
      ]
    }
  }
}
</script>

<style>
.card {
  flex-basis: 210px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 5px;
  margin-right: 10px;
  margin-bottom: 10px;
}
.card img {
  max-width: 100%;
}
.card-content {
  padding: 0 10px;
}
h1 {
  font-size: 23px;
}
p {
  font-size: 14px;
}
</style>
