<template>
    <div>
      <h4>Division</h4>
      <input type="number" v-model.number="value1" class="form-control mb-2" placeholder="Enter first value">
      <input type="number" v-model.number="value2" class="form-control mb-2" placeholder="Enter second value">
      <button class="btn btn-primary" @click="calculer">Calculer</button>
      <div v-if="error" class="mt-3 alert alert-danger">{{ error }}</div>
      <div v-if="result !== null" class="mt-3 alert alert-success">Result: {{ result }}</div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const value1 = ref(0);
      const value2 = ref(0);
      const result = ref(null);
      const error = ref('');
  
      const calculer = () => {
        error.value = '';
        result.value = null;
  
        if (value2.value === 0) {
          error.value = 'Division by zero is not allowed.';
        } else {
          result.value = value1.value / value2.value;
        }
      };
  
      return { value1, value2, result, error, calculer };
    },
  };
  </script>
  