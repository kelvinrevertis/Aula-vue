<script>
import TheHeader from './components/TheHeader.vue'

export default {
  name: 'App',
  components: {
    TheHeader
  },
  data() {
    return {
      showHeader: true,
      name: 'Jon Snow',
      showName: false,
      acessLevel: "marketing"
    }
  }
}

</script>

<template>
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
