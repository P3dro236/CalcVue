<script setup lang="ts">

</script>

<template>
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
</template>

<style scoped>

</style>