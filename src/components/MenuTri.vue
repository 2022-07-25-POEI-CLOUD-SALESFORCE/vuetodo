<template>
  <ul class="tri">
    <li><a @click="showAll">All</a></li>
    <!-- une fonction à laquelle on passe le statut à trier -->
    <li><a @click="show('ended')">Ended</a></li>
    <li><a @click="show('started')">Started</a></li>
    <li><a @click="show('waiting')">Waiting</a></li>
  </ul>
</template>

<script>
  export default {
    name: 'MenuTri',
    methods: {
      // emission d'évènements vers le parent
     showAll() {
      this.$emit('showAll');
     },  
     show(statut) {
      //on passe au parent le statut qu'il faudra trier
      this.$emit('show', statut);
     }
    }
  }
</script>

<style scoped>
  .tri {
    text-align: center;
    list-style-type: none;
  }
  .tri li {
    display: inline-block;
    padding: 5px;
    font-size: 1.5em;
  }
  .tri a {
    text-decoration: underline;
    cursor: pointer;
    color: blue;
  }
</style>