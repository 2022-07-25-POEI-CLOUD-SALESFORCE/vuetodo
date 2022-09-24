<template>
  <div class="todolist">
    <!-- l'UI n'est composée que de composants -->
    <MyHeader titre="Vue Todo"/>
    <!-- on affiche le nombre de tâches via une fonction dans computed 
         on pourrait aussi afficher todos.length -->
    <SlotTodo>{{ nbTodo }}</SlotTodo>
    <!-- récupération des events pour le tri -->
    <MenuTri @showAll="showAll" @show="show"/>
    <!-- methode 'computed' mise en cache pour afficher un message quand il n'y 
         a plus de tâches dans la liste-->
    <h2>{{ hasTodos }}</h2>
    <!-- boucle d'affichage des tâches. Récupération des évents pour traitement dans le parent -->
    <MyTodo v-for="todo in todos" :key="todo.id" :todo="todo" @start='start' @end='end' @del='del' />
    <FormTodo @add="add"/>
    <MyFooter />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import SlotTodo from './components/SlotTodo.vue';
import MenuTri from './components/MenuTri.vue';
import MyTodo from './components/MyTodo.vue';
import FormTodo from './components/FormTodo.vue';
import MyFooter from './components/MyFooter.vue';


export default {
  name: 'App',
  components: {
    MyHeader,
    SlotTodo,
    MenuTri,
    MyTodo,
    FormTodo,
    MyFooter
  },
  data() {
    return {
      todos: [
        {id: 1, nom:'Tache 1', desc: 'description 1', statut: 'waiting'},
        {id: 2, nom:'Tache 2', desc: 'description 2', statut: 'started'},
        {id: 3, nom:'Tache 3', desc: 'description 3', statut: 'waiting'},
        {id: 4, nom:'Tache 4', desc: 'description 4', statut: 'ended'},
        {id: 5, nom:'Tache 5', desc: 'description 5', statut: 'waiting'},
      ],
      //pour les fonctions de tri on sauvegarde la liste des tâches avant
      saveTodos: []
    }
  },
  methods: {
    //ajout d'une tâche depuis le composant FormTodo
    add(todo) {
      todo.id = this.todos.length + 1; 
      console.log(todo);
      this.todos.push(todo);
//      console.log(this.todos);
    },
    // démarrage d'un tâche depuis le composant MyTodo
    start(id) {
      //on fait une boucle sur la liste des tâches. 
      //si on trouve le bon id on change le statut
      this.todos.forEach(function(todo) {
        if(todo.id === id) todo.statut = 'started';
      });
    },
    // arrêt d'une tâche depuis le composant MyTodo
    end(id) {
      this.todos.forEach(function(todo) {
        if(todo.id === id) todo.statut = 'ended';
      });
    },
    // suppression d'une tâche depuis le composant MyTodo
    del(id) {
      //on remet dans todos tous les éléments sauf celui dont l'id est en params
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    // affichage des tâches en fonction du statut
    show(statut) {
      //on remplace la liste complète dans todos avant le tri
      this.todos = this.saveTodos;
      this.todos = this.todos.filter(todo => todo.statut === statut);
    },
    // affichage de toutes les tâches
    showAll() {
      this.todos = this.saveTodos;
    }
  },
  // computed = pas de params et retour obligatoire
  // calculé et mis en cache 
  computed: {
    //affichage du nombre de tâches dans la liste
    nbTodo() {
      return this.todos.length;
    },
    //affichage d'un message si aucune tâche à effectuer
    hasTodos() {
      if(this.todos.length === 0) return "Aucune tâche à effectuer";
      else return null;
    }
  },
  //document ready( sauvegarde de la liste des todos)
  mounted() {
    this.saveTodos = this.todos;
  }

}
</script>

<style>
.todolist {
  width: 40%;
  margin: 0 auto;
  border: 1px solid silver;
  padding: 20px;
}
button {
  margin: 0 auto;
}
</style>
