<script setup>
import HelloWorld from './components/HelloWorld.vue'
import { ref, onMounted} from 'vue';

const value =ref('');
const PrintValue = (event) =>{
  value.value +=event.target.value;
};
const clear = () =>{
  value.value = '';
};
const Delete = () =>{
  value.value = value.value.slice(0,-1);
};
const equal = () =>{
  try{
    value.value = Function('return '+ value.value)();
  }catch{
    value.value = 'Error';
  }
};
onMounted(() =>{
  document.querySelector('.Calculator').classList.add('fade-in');
}

)
</script>

<template>
  
  <div class="Calculator">
  <form>
<div class="display">
  <input type="text" class="screen" v-model="value" readonly >
</div>
<div class=" buttons">
<div class="number">
<input type="button" value="9" @click="PrintValue">
<input type="button" value="8" @click="PrintValue">
<input type="button" value="7" @click="PrintValue">
<input type="button" value="6" @click="PrintValue">
<input type="button" value="5" @click="PrintValue">
<input type="button" value="4" @click="PrintValue">
<input type="button" value="3" @click="PrintValue">
<input type="button" value="2" @click="PrintValue">
<input type="button" value="1" @click="PrintValue">
<input type="button" value="AC" @click="clear">
<input type="button" value="0" @click="PrintValue">
<input type="button" value="DE" @click="Delete">

</div>
<div class="functions">
  <input type="button" value="+" @click="PrintValue">
  <input type="button" value="-" @click="PrintValue">
  <input type="button" value="/" @click="PrintValue">
  <input type="button" value="*" @click="PrintValue">
  <input type="button" value="." @click="PrintValue">

</div>
<input type="button" class="equal" value="=" @click="equal">
</div>




  </form>

    
    
  </div>
  
</template>
<script>

</script>
<style>
body{
background: #213547;
}
.Calculator{
  width: 360px;
  height: 70vh;
  border-radius:25px ;


border:solid 2px #ffff;
}
.display{
  margin-top: 40px;
  display: flex;
  height: 50px;
  width: 100%;
  justify-content: center
  
}

.screen{
width: 80% ;
background: none;
border: none;
border-bottom:solid #ffff;
border-right:solid #ffff;
}
.buttons{
margin-top: 25px;
display: flex;
flex-direction: row;
justify-content: center;
flex-wrap: wrap;



}
.buttons input{
  border-radius: 15px;
  border: none;
  color: #213547;
  background: #ffff;
}

.number{
width: 65%;
display: flex;
flex-direction: row-reverse;
flex-wrap: wrap;
justify-content: space-around;
}
.number input{
margin: 5px;
  width: 60px;

height: 60px;  
}

.functions{
display: flex;
flex-direction: column;
justify-content: space-evenly;

}
.functions input{
  width: 60px;
  height: 50px;
  
  
}
.equal{
  width: 77%;
  height: 60px;
  
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade-in {
  animation: fadeIn 2s ease-in;
}
</style>

