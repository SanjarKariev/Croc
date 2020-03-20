<template>
  <div class="write">
    <input v-model="message">
  </div>
</template>

<script>
import $ from "jquery";

export default {
  name: 'write',
  data(){
    return {
      message: 'Print your text',
    }
  },
}
</script>
