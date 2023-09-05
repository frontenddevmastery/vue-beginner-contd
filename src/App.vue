<script>
import HomePage from './components/Home-page.vue'
export default {
  components: {
    HomePage
  },
  data() {
    return {
      currentPage: 'HomePage',
    }
  },
  computed: {
    renderPage() {
      return this.currentPage
    }
  },
  methods: {
    openHomePage() {
      this.currentPage = 'HomePage'
      return this.currentPage
    }
  }
}
</script>

<template>
  <nav>
    <h1>Vue App</h1>
    <ul>
      <li><a href="#" v-on:click="openHomePage">Home</a></li>
      <li><a href="#" v-on:click="openSignUpPage">Sign up</a></li>
    </ul>
  </nav>

  <!-- <component v-bind:is="renderPage" /> -->
  <Suspense>
    <HomePage />

    <template v-slot:fallback>
      Loading...
    </template>
  </Suspense>

</template>

<style scoped>
body {
  width: 100vw;
}
nav {
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 2px solid wheat;
}
li,
li a {
  display: inline-block;
}
a {
  list-style-type: none;
  display: inline-block;
  font-size: 1.2rem;
}
a:nth-child(1) {
  padding-right: 2rem;
}
.users {
  display: flex;
  flex-wrap: wrap;
}
.users img {
  width: 200px;
  height: 200px;
}
</style>
