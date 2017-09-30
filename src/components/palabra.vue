<template>
  <div class="mensaje_back">
    <div class="mensaje">
      {{texto}}
    </div>
  </div>
</template>

<script>
export default {
  props:['texto']
}
</script>

<style scoped>
.mensaje_back{  
  /*display: inline-block;
  min-width: 50px;*/
  height: 30px;
  width: calc(100% - 10px);
  margin: 5px;
  display: flex;
  align-items: center;
}
.mensaje{
  border-radius: 5px;
  background-color: rgba(15, 105, 18, 0.5);
  border: 1px solid #FAFAFA;
  padding: 3px;
  color: white;
}
</style>