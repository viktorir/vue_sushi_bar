<template>
  <header>
    <a id="logo" href="/">
      <img src="@/assets/logobar.logo.png" height="60"/>
    </a>
    <a id="signin" href="/">Войти</a>
  </header>
  <main></main>
  <footer></footer>
</template>

<script>
export default {

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
</style>
