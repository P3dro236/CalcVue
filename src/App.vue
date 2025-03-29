<script setup lang="ts">
  import { reactive } from 'vue'

  const react = reactive({
    result: 0,
    firstInput: 0,
    lastInput: 0,
    selectedOperation: "+"
  })

  const doOperation = ():void =>{
    switch(react.selectedOperation){
      case "+": react.result = react.firstInput + react.lastInput; break
      case "-": react.result = react.firstInput - react.lastInput; break
      case "*": react.result = react.firstInput * react.lastInput; break
      case "/": react.result = react.firstInput / react.lastInput; break
    }
    if(react.result === Infinity){
      react.result = "Error"
    }
  }
</script>

<template>
  <div class="container d-flex justify-content-center align-items-center pt-5">
    <main class="w-50 h-50 p-5 flex-column d-flex align-items-center justify-content-center text-center mt-5 rounded">
      <h1 class="text-center text-white">{{ react.result }}</h1>
      <div class="wrapper mt-5">
        <div class="row">
          <div class="col-5">
            <input v-model="react.firstInput" type="number" class="form-control" @keyup="doOperation" placeholder="Digite aqui um número">
          </div>
          <div class="col-2">
            <select class="form-control text-center" @change="(e:any) => {
              react.selectedOperation = e?.target.value;
              doOperation();
            }">
              <option value="+" class="text-center" selected>+</option>
              <option value="-" class="text-center">-</option>
              <option value="*" class="text-center">*</option>
              <option value="/" class="text-center">/</option>
            </select>
          </div>
          <div class="col-5">
            <input v-model="react.lastInput" type="number" class="form-control" @keyup="doOperation" placeholder="Digite aqui um número">
          </div>
        </div>
      </div>
    </main>
  </div>
</template>
<style>
  body{
    background-color: rgba(24,24,24,1);
  }
  main{
    background-color: rgb(56, 56, 56);
  }
</style>
