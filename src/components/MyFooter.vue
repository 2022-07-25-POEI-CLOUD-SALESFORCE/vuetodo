<template>
  <footer>
    <p>Copyright &copy;{{dte}} - Moi</p>
  </footer>
</template>

<script>
  export default {
    name: 'MyFooter',
    data() {
      return {
        dte: new Date().getFullYear()
      }
    }
  }
</script>

<style>
  footer {
    text-align: center;
  }
</style>