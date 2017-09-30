<template>
  <div>
    <sala-header></sala-header>
<!------------------------>
    <div class="chat-main">      
       <palabra v-for="mensaje in conversacion" :texto=mensaje.texto :key="mensaje.texto"  >         
       </palabra>
    </div>
<!------------------------>
    <sala-footer :conversacion="conversacion"></sala-footer>
  </div>
</template>

<script>
import salaHeader from './salaHeader.vue'
import salaFooter from './salaFooter.vue'
import palabra from './palabra.vue'
export default {
  data () {
    return {

    }
  },
  props:['conversacion'],
  components:{
    salaHeader,
    salaFooter,
    palabra
  }
}
</script>

<style scoped>
.chat-main{
  height: calc(100% - 100px);
  width: 100%;
  overflow: auto;
}
</style>
