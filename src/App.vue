/* eslint-disable vue/no-unused-components */
<template>
  <div id="app">
    <h1>Developer's skill list</h1>
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>

    <router-view />
  </div>
</template>

<script>
import Skills from './components/Skills.vue'

export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Skills
  }
}
</script>

<style>
body {
  background-color: #808186;
  color: #212329;
  font-family: Avenir, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 20px;
  padding-bottom: 50px;
}
body, html {
  margin: 0;
  height: auto;
}
#app {
  width: 50%;
}

h1 {
  font-size: 3em;
  font-weight: bold;
  color: #ffff;
}

.about h1 {
  font-size: 2em;
  color: #212329;
}

.about p {
  font-size: 1.1em;
}

nav {
  padding: 20px 20px 25px 0;
}

nav a {
  padding: 10px 20px;
  text-decoration: none;
  background: #38B179;
  border-radius: 2px;
  color: #ffff;
  font-weight: bold;
  margin-right: 15px;
}

nav a:hover {
  background: #6AB74F;
}

</style>
