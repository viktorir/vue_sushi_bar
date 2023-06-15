<template>
  <header>
    <a id="logo" href="/">
      <img src="@/assets/logobar.logo.png" alt="Такой себе Суши-бар" height="60"/>
    </a>
    <a id="signin" href="/">Войти</a>
  </header>
  <main>
    <nav>
      <ul class="navbar">
        <li class="navbar__element" v-for="type in productTypes" v-bind:key="type.id_type"><a href="#">{{ type.name }}</a></li>
      </ul>
    </nav>

    <section v-for="type in productTypes" v-bind:key="type.id_type">
      <h2>
        {{ type.name }}
      </h2>
      <div class="section__cards">

        <article class="card" v-for="product in evenProducts(type.id_type)" v-bind:key="product.id_product" >
          <img src="@/assets/card_test.webp" alt="card_img">
          <div class="card__info">
            <div class="description">
              <h3>{{ product.name }}</h3>
              <p>{{ product.description }}</p>
            </div>
            <b class="price">{{ product.price }}</b>
          </div>
        </article>

      </div>
    </section>
  </main>
  <footer></footer>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      productTypes: [],
      products: []
    }
  },
  mounted() { 
    axios.get(`http://localhost:8080/api/product_type`).then(res => (this.productTypes = res.data));
    axios.get(`http://localhost:8080/api/product`).then(res => (this.products = res.data));
  },
  methods: {
    evenProducts(type) {
      return this.products.filter(products => products.type_id === type)
    }
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

  padding: 10px 10%;
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
  padding: 10px 10%;

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

section {
  margin: 0 10%;
  margin-top: 20px;
  
}

h2 {
  margin: 0;
}

.section__cards {
  display: flex;
  justify-content: flex-start;
  flex-direction: row;
  flex-wrap: wrap
}

.card {
  max-width: 22.5%;
  margin-bottom: 10px;
  margin-right: 2.5%;
  box-shadow: 0px 5px 5px -5px rgba(34, 60, 80, 0.6);
}

.card__info {
  margin-bottom: 10px;
}

img {
  max-width: 100%;

  object-fit: cover;
  object-position: 50% 50%;
}

</style>
