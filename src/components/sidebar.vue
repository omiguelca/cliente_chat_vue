<template>
  <div>
    <header>
      <div class="usuario_avatar glyphicon glyphicon-user "></div>
      <div class="usuario_nombre">
        {{ usuario.nombre }}
      </div>
    </header>
    <div class="nav-side-menu">
      <div class="grupos_titulo">{{grupos_titulo}}</div>
      <input type="text" 
      v-model="newGrpCto" 
      v-on:keyup.enter="addGrp" 
      placeholder="Nombre del Grupo" 
      style="width:100%;height:1.5em;display:none"
      >
      <ul class="collapsed active">
        <li v-for="(grupo, index) in grp_contactos" :key="grupo.nombre " 
        data-toggle="collapse" 
        :data-target="grupo.nombre"
        class="collapsed active">
            <a href="#">
              {{ grupo.nombre }}
            <ul class="sub-menu collapse" :id='grupo.nombre'>
              <li v-for="(contacto, index) in grupo.contactos" :key="contacto.nombre" class="active">
                {{ contacto.nombre }}
              </li>
            </ul>
            </a>
        </li>                    
      </ul>
      
    </div>  
  </div>
</template>

<script>
export default {  
  data () {
    return {
      newGrpCto:''
    }
  },
  props:['grp_contactos','usuario','grupos_titulo'],  
  methods: {
      addGrp() {
        var texto = this.newGrpCto.trim();
        if(texto){
          this.grp_contactos.push({nombre:texto});
          //vincular con el servicio de grabar grupo de contactos del usuario
        }
        this.newGrpCto = '';        
    }
  }
}
</script>

<style>
.grupos_titulo{
  background-color: #EEE;
  text-align: center;
}
.usuario_avatar{
  color: white;
  background-color: rgba(255,0,0,.5);
  border-radius: 50%;
  margin-left:50px ;
  width: 100px;
  height: 100px;
  text-align: center;
  font-size: 70px;
  padding: 5px;
}
.usuario_nombre{
  color: white;
  width: 100%;
  font-size: 1.2em;
  text-align: center;
}
.nav-side-menu{
  background-color: rgba(255,255,255,.5);
  border: 1px solid #000;
  border-radius: 5px;
  width: 95%;
  height: calc(95% - 100px - 1em);
  margin: auto; 
  overflow: auto;
}
.nav-side-menu ul,
.nav-side-menu li {
  list-style: none;
  padding: 0px;
  margin: 0px;
  line-height: 35px;
  cursor: pointer;
}
.nav-side-menu ul :not(collapsed) .arrow:before,
.nav-side-menu li :not(collapsed) .arrow:before {
  font-family: FontAwesome;
  content: "\f078";
  display: inline-block;
  padding-left: 10px;
  padding-right: 10px;
  vertical-align: middle;
  float: right;
}
.nav-side-menu ul .active,
.nav-side-menu li .active {
  border-left: 3px solid #d19b3d;
  background-color: #4f5b69;
}
.nav-side-menu ul .sub-menu li.active,
.nav-side-menu li .sub-menu li.active {
  color: #d19b3d;
}
.nav-side-menu ul .sub-menu li.active a,
.nav-side-menu li .sub-menu li.active a {
  color: #d19b3d;
}
.nav-side-menu ul .sub-menu li,
.nav-side-menu li .sub-menu li {
  background-color: #181c20;
  border: none;
  line-height: 28px;
  border-bottom: 1px solid #23282e;
  margin-left: 0px;
}
.nav-side-menu ul .sub-menu li:hover,
.nav-side-menu li .sub-menu li:hover {
  background-color: #020203;
}
.nav-side-menu ul .sub-menu li:before,
.nav-side-menu li .sub-menu li:before {
  font-family: FontAwesome;
  content: "\f105";
  display: inline-block;
  padding-left: 10px;
  padding-right: 10px;
  vertical-align: middle;
}
.nav-side-menu li {
  padding-left: 0px;
  border-left: 3px solid #2e353d;
  border-bottom: 1px solid #23282e;
}
.nav-side-menu li a {
  text-decoration: none;
  color: #e1ffff;
}
.nav-side-menu li a i {
  padding-left: 10px;
  width: 20px;
  padding-right: 20px;
}
.nav-side-menu li:hover {
  border-left: 3px solid #d19b3d;
  background-color: #4f5b69;
  -webkit-transition: all 1s ease;
  -moz-transition: all 1s ease;
  -o-transition: all 1s ease;
  -ms-transition: all 1s ease;
  transition: all 1s ease;
}
</style>