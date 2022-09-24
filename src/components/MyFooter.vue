<template>
  <footer>
    Copyright &copy;{{dte}} - Moi
  </footer>
</template>

<script>
  export default {
    name: 'MyFooter',
    data() {
      return {
        //date dynamique
        dte: new Date().getFullYear()
      }
    }
  }
</script>

<style>
  footer {
    height: 30px;
    line-height: 30px;
    text-align: center;
    background: black;
    color: white; 
  }
</style>