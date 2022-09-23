<template>
  <header>
    <img src="../assets/logo.png" alt='Vue Todo' />
    <h1>{{ titre }}</h1>
  </header>
</template>

<script>
  // on passe le titre sous forme de props pour avoir un composant à copier/coller dans chaque projet
  export default {
    name: 'MyHeader',
    props: {
      titre: String
    }
  }
</script>

<style>
  header {
    display: flex;
  }
  header img {
    width: 100px
  }
</style>