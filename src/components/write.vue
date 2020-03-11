<template>
<div class="write">
  <p>{{ message }}</p>
  <input v-model="message">
</div>
</template>

<script>
export default {
  name: 'write',
  data(){
    return {
        message: 'Print your text',
    }
  },
}
</script>
