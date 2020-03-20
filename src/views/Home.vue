<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <write/>
    <p>{{datasend}}</p>
    <button type="button" name="button" @click='ajax'>Get to server</button>
  </div>
</template>

<script>
// @ is an alias to /src
import write from '@/components/write.vue';
import $ from "jquery";

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
      datasend: '!!!ERROR!!!',
    }
  },
  methods: {
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
