<script setup>
import {reactive} from 'vue';

const estado = reactive ({
  operacao: ['soma','resta','multiplicar','dividir'],
  primero : '',
  segundo: '',
  mensagem: 'Elige una operacion',
});
function soma(x,y){
  return estado.primero + estado.segundo;
};
function resta(x,y){
  return estado.primero - estado.segundo;
};
function multiplicar(x,y){
  return estado.primero * estado.segundo;
}
function dividir(x,y){
  return estado.primero / estado.segundo;
}
const getOperacao = () =>{
  const {operacao} = estado;
  switch (operacao){
    case 'soma':
      return soma();
    case 'resta':
      return resta();
    case 'multiplicar':
      return multiplicar();
    case 'dividir':
      return dividir();
    default:
      return estado.mensagem;
  }
}
</script>

<template>
  <header>
    <h1>Calculadora</h1>
  </header>
  
  <main>
    <div class="container">
        <br>
      <form>
        <label for="operacao">Por favor seleciona a operacao desejada</label>
        <select @change="evento => estado.operacao = evento.target.value" >
          <option :value="estado.operacao.mensagem"></option>
          <option value="soma" >Soma</option>
          <option value="resta" >Resta</option>
          <option value="multiplicar" >Multiplicar</option>
          <option value="dividir" >Dividir</option>
        </select><br>

        
        <label for="primeiro">Digita o primeiro número</label>
        <input :value="estado.primero" @keyup="evento => estado.primero = evento.target.value" required type="text" placeholder="00" class="form-control"><br>
        <label for="segundo">Digita o segundo número</label>
        <input :value="estado.segundo" @keyup="evento => estado.segundo = evento.target.value" required type="text" placeholder="00" class="form-control"><br>
        
        
      </form>
      <p id="resultado">Resultado: 
      
      {{ getOperacao(primero,segundo) }}
    </p>
  
    </div>
    
  </main>
</template>

<style scoped>
h1{
  font-size: 40px;
  text-align: center;
}
.container
{
  width:400px;
  border:2px solid #000;
  padding: 16px;
  background-color: #999;
  margin:20px auto;
}input, select{
  margin-bottom: 10px;
  margin-left: 5px;
  background-color: #c9c4c4;
  padding: 6px;
  color:#333;
}
#resultado{
  font-size: 22px;

}
</style>
