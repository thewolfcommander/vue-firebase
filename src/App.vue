<template>
  <div id="app">
    <Navbar />
    <h1>Welcome</h1>
    <h3><strong>I am {{ name }}</strong> and I am {{ age }} years old.</h3>
    <p>{{ bio }}</p>
    <Blogs />
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import Blogs from './components/Blogs'

export default {
  name: 'App',
  components: {
    Navbar,
    Blogs
  },
  data() {
    return {
      name: 'Manoj',
      age: 20,
      bio: 'I am a full stack developer and I have very strong hands in Django. I am currently learning Vue.js',
    }
  },
  methods: {

  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}


</style>

