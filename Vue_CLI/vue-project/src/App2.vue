<template>
  <h1>Teste</h1>

  <div>
    <input v-model="name2" type="text">
    <br>
    {{name2}}
  </div>

  <div>
    <input v-model="name3" type="text">
    <br>
    {{name3}}
  </div>
  <br><br>

  <div>
    <input v-model="user.first_name" type="text">
  </div>

  <div>
    <input v-model="user.last_name" type="text">
    <br>
    {{user.first_name +" "+ user.last_name}}
  </div>
  <br><br>

  <select v-model="pageCount">
    <option value="5">5</option>
    <option value="10">10</option>
    <option value="15">15</option>
  </select><br>
  {{ pageCount }}

  <div>
    <br><br><br>
    <div>
      {{fullName}}
    </div>

    <h2>TODOS EM ABERTO</h2>
    <div v-for=" todo in uncompletedTodos" :key="todo.id" class="todos-item">

      {{ todo.title }}

    </div>
    <br><br>

    <h2>TODOS COMPLETOS</h2>
    <div v-for=" todo in completedTodos" :key="todo.id" class="todos-item">

      {{ todo.title }}

    </div>
    <br><br>

    <div v-for=" todo in todos" :key="todo.id" class="todos-item">

      <input v-model="todo.completed" type="checkbox">

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

    </main>



  </div>
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
      name2: '',
      name3: '',
      showHeader: true,
      name: 'Jon Snow',
      showName: false,
      acessLevel: "marketing",
      pageCount: 5
    }
  },

  watch: {
    name2(newValue, oldValue) {
      console.log(newValue, oldValue)
    },
    name3(vl) {
      if (vl.length >= 3) {
        this.savesUserName()
      }

    },
    pageCount() {
      this.changePage()
    },
    user: {
      handler() {
        console.log('User alterado!')
      },
      deep: true
    },
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
  },
  methods: {
    savesUserName() {
      console.log('Ajax')
      console.log(this.name3)
    },
    changePage() {
      console.log('Ajax changePage')
    }
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
