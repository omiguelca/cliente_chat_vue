<template>
  <div id="app">
    <sidebar class="sidebar" :grp_contactos="grp_contactos" :usuario="usuario" :grupos_titulo="grupos_titulo"/>
    <sala v-if="contacto.nombre.length>0" class="sala" :conversacion="conversacion"/>
  </div>
</template>

<script>
import sidebar from './components/sidebar.vue'
import sala from './components/sala.vue'
export default {
  name: 'app',
  components:{
    sidebar,
    sala
  },
  data () {
    return {
      usuario:{avatar:'',nombre:'omiguelca'},
      grupos_titulo:'Grupos de Contacto',      
      grp_contactos:[
          {nombre:'Familia',contactos:[{nombre:'Tio'},{nombre:'Primo'}]},
          {nombre:'Trabajo'},
          {nombre:'Escuela'}
          ],
      contacto:{avatar:'',nombre:'Amigo'},
      conversacion:[],
      mensaje:{texto:'',formato:''}
    }
  }
}
</script>
<style>
body, html, #app{
  height: 100%;
}
</style>

<style>
.sidebar{
  color:#000;
  background-color: #2F3E4F;
  float:left;
  width: 200px;
  height: 100%;
}
.sala{
  background-color:#DDD;
  width: calc(100% - 200px);
  float:left;
  height: 100%;
}
</style>

