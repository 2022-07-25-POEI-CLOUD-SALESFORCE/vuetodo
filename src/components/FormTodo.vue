<template>
  <div>
    <p>
      <label>Name</label>
      <input v-model="newTodo.nom" />
    </p>
    <p>
      <label>Description</label>
      <input v-model="newTodo.desc" />
    </p>
    <p>
      <button @click="add">Add</button>
    </p>
  </div>  
</template>

<script>
  export default {
    name: 'FormTodo',
    data() {
      return {
        newTodo: {statut: 'waiting'}
      }
    },
    methods: {
      add(){
        //console.log(this.newTodo);
        this.$emit('add', this.newTodo);
        this.newTodo = {statut: 'waiting'};
      }
    }
  }
</script>

<style scoped>
  
</style>