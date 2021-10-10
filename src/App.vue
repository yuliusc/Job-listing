<template>
  <div id="app">

    <header>
      <img src="../public/images/bg-header-desktop.svg" class="header--desktop">
      <img src="../public/images/bg-header-mobile.svg" class="header--mobile">

    </header>

    <Cards/>
  </div>
</template>

<script>
import Cards from './components/Cards.vue'

export default {
  name: 'App',
  components: {
    Cards,
  }
}
</script>

<style>
@import "styles/general.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
header{
  background: #5CA5A5;
}
header img{
  width: 100%;
}
@media (min-width: 575px) {
  .header--desktop {
    display: block
  }
  .header--mobile {
    display: none;
  }
}

@media (max-width: 575px) {
  .header--mobile {
    display: block;
  }
  .header--desktop {
    display: none
  }
}

</style>
