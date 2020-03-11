<template>
    <div id="app">
        <p v-if='sanjar'>goodbye sanjar</p>
        <p v-if='!sanjar'>hallo sanjar</p>
        <img alt="sanjar" src="./assets/logo.png" v-if='!sanjar'>
        <img alt="redClick" src="./assets/redClick.png" @click='datafunc'>
        <revers/>
        <write/>
    </div>
</template>

<script>
import greeting from './components/greeting.vue';
import revers from './components/revers.vue';
import write from './components/write.vue';
import $ from "jquery";

export default{
  name: 'app',
  components: {
    greeting,
    revers,
    write,
  },
  data() {
    return {
      sanjar: true,
    }
  },
  methods: {
    async datafunc(){
      // отправим данные
      let xhr = new XMLHttpRequest();
      xhr.open("GET", "http://localhost:8080/api/timeJSON");
      xhr.send();

      xhr.onload = () => console.log('xhr.response');

    },
    doIt(){
    console.log('works properly');
      let vm = this;
      vm.sanjar = !vm.sanjar;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
