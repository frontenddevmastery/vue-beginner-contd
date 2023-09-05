<script>
import { ref, reactive } from 'vue'
export default {
  async setup() {
    const data = await fetch('https://jsonplaceholder.typicode.com/photos/1')
    const response = await data.json()
    const state = reactive({ title: response.title })

    function changeTitle() {
      state.title = 'A person'
      return state.title
    }
    return { state, response, changeTitle }
  },
  created() {}
}
</script>

<template>
  <div class="home">
    <h1>This is the Home up page</h1>
    <p>
      Home page Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam quisquam officiis
      excepturi cum iusto illum voluptates vero omnis rem tenetur nesciunt, numquam, perferendis
      quaerat expedita?
    </p>

    <section class="users">
      <img v-bind:src="response.thumbnailUrl" v-bind:alt="response.title" loading="lazy" />
      <p>{{ response.title }}</p>
    </section>

    <h2>{{ state.title }}</h2>
    <button @click="changeTitle">Change Title</button>

    <pre>{{ response }}</pre>
  </div>
</template>

<style scoped>
.home {
  width: 75%;
}
</style>
