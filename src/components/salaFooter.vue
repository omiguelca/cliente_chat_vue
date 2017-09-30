<template>
  <footer>
    <div class="recursos glyphicon glyphicon-picture"></div>
    <div class="iconos"></div>
    <div class="directo">
      <a class="glyphicon glyphicon-thumbs-up"></a>
      <a class="glyphicon glyphicon-thumbs-down"></a>        
    </div>
    <div class="formato glyphicon" :class="{'glyphicon-expand':formato,'glyphicon-align-left':!formato}"
      v-on:click="cambiaFormato">       
    </div>
    <div class="input">
      <input 
          type="text" 
          placeholder="Escribe una Mensaje"
          v-model="mensaje"
          v-on:keyup.enter="agregaMensaje">
    </div>
    <div class="envia glyphicon glyphicon-send"></div>
  </footer>
</template>

<script>
export default {
  data () {
    return {
      mensaje:'',
      formato:false
    }
  },
  props:['conversacion'],
  methods:{
    cambiaFormato(){
      this.formato = !this.formato;
    },
    agregaMensaje(){
      var texto = this.mensaje.trim();
      if(texto){
        this.conversacion.push({texto:texto});
      }
      var objDiv = document.getElementsByClassName("chat-main");
      //var objDiv = this.$el.querySelector(".chat-main");
      objDiv[0].scrollTop = objDiv[0].scrollHeight-30;
      this.mensaje='';
    }
  }
}
</script>

<style scoped>
footer{
  height: 50px;
  width: 100%;
  font-size: 25px;
  background-color: #CCC;
}
.recursos{float: left;margin-left:10px;}
.iconos{float: left;margin-left:10px;}
.directo{float: left;margin-left:10px;}
.input{float: left;margin-left:10px;}
.envia{float: right;margin-left:10px;margin-right:10px;}
.formato {float: left; margin-left:10px;cursor: pointer}
.formato:hover{ font-size: 1.3em;}
</style>
