<template>
  <button 
    style="background-color: green" class="btn"
    @click="$emit('btn-click')"
  >
      {{text}}
  </button>
</template>


<script>
  export default {
    name: 'Button',
    props:{
      text: {
        type: String,
        default: 'Click'
      }
    }
  }
</script>