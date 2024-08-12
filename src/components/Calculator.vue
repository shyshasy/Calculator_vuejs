<template>
    <div class="container mt-5">
      <!-- <h2>VueJS Calculator</h2> -->
      
      <div class="mb-3">
        <h4>Choisissez une operation:</h4>
        <div>
          <input type="radio" id="add" value="add" v-model="operation">
          <label for="add">Addition</label>
  
          <input type="radio" id="subtract" value="subtract" v-model="operation">
          <label for="subtract">Soustraction</label>
  
          <input type="radio" id="multiply" value="multiply" v-model="operation">
          <label for="multiply">Multiplication</label>
  
          <input type="radio" id="divide" value="divide" v-model="operation">
          <label for="divide">Division</label>
        </div>
      </div>
  
      <!-- Affichage du composant d'opération sélectionné -->
      <div v-if="operation === 'add'">
        <Addition />
      </div>
      <div v-if="operation === 'subtract'">
        <Subtraction />
      </div>
      <div v-if="operation === 'multiply'">
        <Multiplication />
      </div>
      <div v-if="operation === 'divide'">
        <Division />
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import Addition from './operations/Addition.vue';
  import Subtraction from './operations/Subtraction.vue';
  import Multiplication from './operations/Multiplication.vue';
  import Division from './operations/Division.vue';
  
  export default {
    components: {
      Addition,
      Subtraction,
      Multiplication,
      Division,
    },
    setup() {
      const operation = ref('');
  
      return { operation };
    },
  };
  </script>
  <style setup>
  .container {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f7f7f7;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  }
  
  h2 {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
  }
  
  label {
    font-weight: bold;
  }
  
  input[type="radio"] {
    margin-right: 10px;
  }
  
  button {
    width: 100%;
    margin-top: 10px;
  }
  
  .alert {
    text-align: center;
  }
  
  input[type="number"] {
    border-radius: 5px;
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 15px;
    width: calc(100% - 20px);
  }
  
  button.btn-primary {
    background-color: #007bff;
    border-color: #007bff;
    border-radius: 5px;
    padding: 10px 0;
    font-size: 16px;
    transition: background-color 0.3s;
  }
  
  button.btn-primary:hover {
    background-color: #0056b3;
  }
  
  .mt-3 {
    margin-top: 15px;
  }</style>