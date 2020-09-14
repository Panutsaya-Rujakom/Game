<template>
  <div id="app">
    <img class="rounded-circle" src="./assets/Pokemon.png" width="20%" />
    <HelloWorld msg="POKEMON" />
    <h6 class="text-light">สุ่มตัวละคร</h6>
    <br>
    <div>
      <botton />
    </div>
    
  </div>
</template>
<script>
import HelloWorld from "./components/HelloWorld.vue";
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    botton,
  },
};
</script>
<style>
#app {
  background-color:#82E0AA;
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}

</style>
