<template>
  <div class="door-area">

<div class="door-frame" :class="{selecionada: selecionada && !aberta}">

    <Gift v-if ="aberta && hasGift"/>

</div>

<div class="door" :class="{aberta}" @click="selecionada = !selecionada">

    <div class="numero" :class="{selecionada}">{{numero}}</div>
    <div class="knob" :class="{selecionada}" @click="aberta = true"></div>

</div>

  </div>
</template>

<script>

import Gift from './Gift';

export default {

name:'Door',
components: {Gift},

props: {
    numero:{},
    hasGift :{type: Boolean}
},
data: function(){
    return {
        aberta: false,
        selecionada :false
        
    }
}

}
</script>

<style>
:root {
    --door-border : 5px solid brown;
    --selecionada-borda:5px solid yellow;
}
.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid #AAA;
    margin-bottom:20px;
    font-size: 3rem;

    display: flex;
    justify-content: center;

}

.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;

    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);

   display: flex;
   justify-content: center;
   align-items: flex-end;
}
.door {
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background-color: chocolate;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}
.door .knob {
    height: 20px;
    width: 20px;
    border-radius:10px;
    background-color:brown;
    align-self: flex-start;
    margin-top:60px;

}
.door-frame.selecionada {
    border-left:var(--selecionada-borda);
    border-top:var(--selecionada-borda);
    border-right:var(--selecionada-borda)
}
.door .numero.selecionada {
   color:yellow;
   }
.door .knob.selecionada {
   background-color: yellow;
}
.door.aberta {
    background-color: #0007;
}
.door.aberta .knob {
    display: none;
}
.door.aberta .numero {
    display: none;
}

</style>