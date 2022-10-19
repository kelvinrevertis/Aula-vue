<template>

  <br><br>
  <div>
    {{fullName}}
  </div>

  <h2>TODOS EM ABERTO</h2>
  <div v-for=" todo in uncompletedTodos" :key="todo.id" class="todos-item">

    {{ todo.title }} 

  </div>
  <br><br>

  <H2>TODOS COMPLETOS</H2>
  <div v-for=" todo in completedTodos" :key="todo.id" class="todos-item">

    {{ todo.title }} 

  </div>
  <br><br>

  <div v-for=" todo in todos" :key="todo.id" class="todos-item">

    <input v-model="todo.completed" type="checkbox" >
    
    {{ todo.title }}

  </div>

  <TheHeader v-if="showHeader" />
  <div v-show="showName">Nome: {{name}}</div>
  <header>
    <div class="wrapper">

    </div>
  </header>


  <div v-if="acessLevel === 'admin'">Admin</div>
  <div v-else-if="acessLevel=== 'marketing'">Marketing</div>
  <div v-else="acessLevel==='user'">User</div>

  <main>
    <TheWelcome />
  </main>




</template>


<script>
import TheHeader from './components/TheHeader.vue'

export default {
  name: 'App',
  components: {
    TheHeader
  },
  data() {
    return {
      user: {
        first_name: 'Jon',
        last_name: 'Snow',
      },
      todos: [
        {
          "imgSrc": 'https://via.placeholder.com/150',
          "imgAlt": 'Foto de Jon Snow',
          "userId": 1,
          "id": 1,
          "title": "delectus aut autem",
          "completed": true
        },
        {
          "imgSrc": 'https://via.placeholder.com/150',
          "userId": 1,
          "id": 2,
          "title": "quis ut nam facilis et officia qui",
          "completed": false
        },
        {
          "userId": 1,
          "id": 3,
          "title": "fugiat veniam minus",
          "completed": false
        },
        {
          "userId": 1,
          "id": 4,
          "title": "et porro tempora",
          "completed": true
        },
        {
          "userId": 1,
          "id": 5,
          "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
          "completed": false
        }
      ],
      showHeader: true,
      name: 'Jon Snow',
      showName: false,
      acessLevel: "marketing"
    }
  },
  computed: {
    fullName() {
      return `${this.user.first_name} ${this.user.last_name}`
    },
    uncompletedTodos() {
      return this.todos.filter(todo => !todo.completed)
    },
    completedTodos() {
      return this.todos.filter(todo => todo.completed)
    },
  }
}

</script>



<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
