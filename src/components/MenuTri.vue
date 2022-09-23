<template>
  <div class="tri">
    <a @click="showAll">All</a> | 
    <a @click="show('ended')">Ended</a> | 
    <a @click="show('started')">Started</a> | 
    <a @click="show('waiting')">Waiting</a>
  </div>
</template>

<script>
  export default {
    name: 'MenuTri',
    methods: {
     showAll() {
      this.$emit('showAll');
     },  
     show(statut) {
      this.$emit('show', statut);
     }
    }
  }
</script>

<style scoped>
  .tri {
    text-align: center;
  }
  .tri a {
    text-decoration: underline;
    cursor: pointer;
    color: blue;
  }
</style>