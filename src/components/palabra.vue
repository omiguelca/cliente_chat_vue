<template>
  <div class="palabra">
    <div class="margen">
      {{texto}}
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      
    }
  },
  props:['texto']
}
</script>

<style scoped>
.margen{
  background-color: #DDD;
  width: 50px;
  height: 50px;
}
</style>