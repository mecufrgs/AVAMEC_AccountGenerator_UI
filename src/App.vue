<template>
  <div id="app">
    <div class="logo-container">
      <img class="logo" alt="logo" src="./assets/logo.png">
      <div class="title">Gerador de contas para a plataforma AVAMEC</div>
    </div>
    <MainPage/>
  </div>
</template>

<script>
import MainPage from './components/MainPage.vue'

export default {
  name: 'app',
  components: {
    MainPage
  }
}
</script>

<style>
#app {
  font-family: "Times New Roman", Times, serif;
  color: #2c3e50;
}

.logo-container{
  background-color: cadetblue;
  height: 10em;
  padding-top: 1%;
  padding-bottom: 1%;
  width: 100%;
}

.logo{
  width: 6em;
  margin-left: 6em;
  float: left;
}

.title{
  margin-right: 20em;
  margin-top: 1em;
  float: right;
  font-weight: 900;
  font-size: 2.1em;
}

@media only screen and (max-width: 1600px) {
  .title {
    margin-right: 10em;
    margin-top: 0.5em;
  }
  .logo{
    width: 4em;
  }
  .logo-container{
    height: 7em;
  }
}
</style>
