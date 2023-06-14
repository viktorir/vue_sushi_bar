<template>
  <header>
    <a id="logo" href="/">
      <img src="@/assets/logobar.logo.png" height="60"/>
    </a>
    <a id="signin" href="/">Войти</a>
  </header>
  <main>
    <ul class="navbar">
      <li class="navbar__element" v-for="type in productTypes" v-bind:key="type.id_type"  :id="type.id_type"><a href="#">{{ type.name }}</a></li>
    </ul>
  </main>
  <footer></footer>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      productTypes: null
    }
  },
  mounted() { 
    axios.get(`http://localhost:8080/api/product_type`).then(res => (this.productTypes = res.data));
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
}

header {
  height: 80px;

  box-shadow: 0 4px 10px rgba(0, 0, 0, .1);

  padding: 10px 40px;
  margin-bottom: 10px;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

#signin {
  text-decoration: none;

  color: red;
  font-size: 36px;
  font-family: sans-serif;
}

.navbar {
  list-style-type: none;
  margin: 0;
  padding-bottom: 10px;
  padding-left: 0;

  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-evenly;

  border-bottom: 1px solid rgba(0, 0, 0, .1);
}

.navbar__element a {
  text-decoration: none;
  color: black;

  font-family: sans-serif;
  font-size: 1.4rem;
}
</style>
