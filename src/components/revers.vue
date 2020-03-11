<template>
  <div class="revers">
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>
</template>
<script>
export default{
  name: 'revers',
    data(){
      return{
        message: 'привет ле',
      }
    },
    methods: {
      reverseMessage: function () {
        this.message = this.message.split('').reverse().join('');
    }
  }
}
</script>
