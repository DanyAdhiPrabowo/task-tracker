<template>
  <button 
    :style="{background: color}" class="btn"
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
      },
      color: String
    }
  }
</script>