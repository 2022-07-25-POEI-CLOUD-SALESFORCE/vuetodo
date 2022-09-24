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
    <p class="btn">
      <button @click="add">Add</button>
    </p>
  </div>  
</template>

<script>
  export default {
    name: 'FormTodo',
    data() {
      return {
        //variable objet pour le formulaire, qui sera retournée au parent au click sur le bouton
        newTodo: {statut: 'waiting'}
      }
    },
    methods: {
      add(){
        //console.log(this.newTodo);
        //envoi d'un évènement vers le parent, contenant l'objet rempli par le formulaire
        this.$emit('add', this.newTodo);
        // remise à blanc du formulaire en effaçant les valeurs des champs
        this.newTodo = {statut: 'waiting'};
      }
    }
  }
</script>

<style scoped>
  label {
    display: block;
    font-size: 1.2em;
  }
  input {
    width: 100%;
    height: 25px;
    font-size: 1.2em;
    border-radius: 5px;
  }
  .btn {
    text-align: center;
  }
  button {
    border-color: white;
    background: black;
    color: white;
    padding: 10px;
    margin: 2px;
  }
</style>