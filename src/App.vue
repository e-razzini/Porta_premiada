<template>
  <div id="app">
    <h1>problema monty hall</h1>
 
<div class="form">

  <div v-if="!iniciado">

   <h3 class="subtitulo" v-if="portaSelecionada <= 0 || portaSelecionada > qtdPortas">{{mensagem}} 0 - {{qtdPortas}}.</h3>  

    <label for="qtdPortas">Quantas Portas?</label>
    <input type="text"  id="qtdPortas" size="3" v-model.number="qtdPortas" >
  </div>

<div v-if="!iniciado">

  <label for="portaSelecionada">Qual a porta premiada?</label>
  <input type="password"  id="portaSelecionada" size="3" v-model.number="portaSelecionada "> 
</div>

<button v-if="!iniciado" @click="iniciado = true">Iniciar game!</button>
<button v-if="iniciado" @click="iniciado = false">Reiniciar game!</button>
</div>

<div class="doors" v-if="portaSelecionada < 1 || portaSelecionada > qtdPortas ? iniciado = false : iniciado">

<div  v-for="i in qtdPortas" :key="i">  
<Door :hasGift="i === portaSelecionada" :numero="i"/> 
</div>

</div>

  </div>
</template>

<script>
import Door from "./components/Door";

export default {
  name: "app",
  components: { Door },

  data:function(){

    return{
    iniciado:false,
    qtdPortas:3,
    portaSelecionada:null,
    mensagem:"Digite um numero entre :" 
    }
      
},

}
</script>

<style>

* {
  box-sizing: border-box;
  font-family: "Titillium Web", sans-serif; 
   
}
body {
  color: #fff;
  background: linear-gradient(
    90deg,
    rgba(180, 58, 93, 1) 10%,
    rgba(253, 71, 29, 0.9575980050223214) 50%,
    rgba(252, 97, 69, 1) 75%
  );
}
.form .subtitulo{  
  font-family: 'PT Mono', monospace;
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  margin-bottom: 60px;
}
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}
.form, .form input, .form button {
  margin-bottom: 10px;
  font-size:2rem;
  text-align: center;
}
.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.form button {
  border-radius: 5px;
  color: #fff;
  background: linear-gradient(
    90deg,
    rgba(180, 58, 93, 1) 10%,
    rgba(253, 71, 29, 0.9575980050223214) 50%,
    rgba(252, 97, 69, 1) 75%
  );
}



</style>