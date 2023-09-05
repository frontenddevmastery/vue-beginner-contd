<script>
import SignUp from './components/Sign-up.vue'
import HomePage from './components/Home-page.vue'
export default {
  components: {
    SignUp,
    HomePage
  },
  data() {
    return {
      currentPage: 'HomePage',
      jsonData: null
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
    },
    openSignUpPage() {
      this.currentPage = 'SignUp'
      return this.currentPage
    },
    async loadData() {
      const data = await fetch('https://jsonplaceholder.typicode.com/photos/1')
      const response = await data.json()
      this.jsonData = response
      return this.jsonData
    }
  },
  created() {
    this.loadData()
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

  <component v-bind:is="renderPage" />

  <section class="users">
    <img v-bind:src="jsonData.thumbnailUrl" v-bind:alt="jsonData.title" loading="lazy" />
    <p>{{ jsonData.title }}</p>
  </section>

  <pre>{{ jsonData }}</pre>
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
