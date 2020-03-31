<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <write/>
    <p>{{datasend}}</p>
    <button type="button" name="button" @click='ajax'>Get to server</button>
    <br/>
    <button @click='CallBlock' type="button" name="button1">Description</button>
    <!-- тут у нас жесты  -->
    <div v-touch:swipe.top="tapHandler" v-touch:swipe.bottom="EndHandler" class="BlockToTop">

    </div>
  </div>
</template>

<script>
import Vue from 'vue'
// @ is an alias to /src
import write from '@/components/write.vue';
import $ from "jquery";

import Vue2TouchEvents from 'vue2-touch-events'

Vue.use(Vue2TouchEvents)

export default {
  name: 'Home',
  components: {
    write,
  },

  mounted() {
    const vm = this;
    vm.ajax()
  },
  data() {
    return {
      datasend: 'not conect server',
    }
  },
  methods: {
    // тут функция свайпа в верх
    tapHandler(){
      console.log('tapHandler');
      $('.BlockToTop').css({
        "height": "80vh"
      })
    },

    // тут функция свайпа в низ
    EndHandler(){

      console.log($('.BlockToTop')[0].clientHeight);

      if ($('.BlockToTop')[0].clientHeight > 61 ) {
        $('.BlockToTop').css({
          "height": "60px"
        })
      } else {
        $('.BlockToTop').css({
          "visibility": "hidden"
        })
      }


    },
    CallBlock(){
      $('.BlockToTop').css({
        "visibility": "visible"
      })
    },
    ajax() {
      const vm = this;
      $.ajax({
        type: "GET",
        url: `http://localhost:8080/api/time`,
        CrossDomain: true,
        success: function(data) {
          console.log(data);
          vm.datasend = data;
        },
      });
    },
  }
}
</script>
<style scoped>
  .BlockToTop{
    width: 90%;
    height: 60px;
    left: 5%;
    position: absolute;
    bottom: 5vh;
    background: #0004;
    cursor: pointer;
    transition: all 0.3s;
  }
   button {
     width: 250px;
     margin: 4px;
   }
</style>
