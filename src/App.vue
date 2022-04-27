<script setup>
import Friends from "./components/Friends.vue";
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";
import Banner from "./components/Banner.vue";
import Cards from "./components/Cards.vue";
</script>

<template>
  <div>
    <Friends />
    <Header />
    <Cards />
    <Banner />
    <Content />
  </div>
</template>


<style lang="scss">
@import "assets/styles";

#app {
  font-family: "Varela Round", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>


