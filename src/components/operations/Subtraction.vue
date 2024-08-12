<template>
    <div>
      <h4>Sousbtraction</h4>
      <input type="number" v-model.number="value1" class="form-control mb-2" placeholder="Enter first value">
      <input type="number" v-model.number="value2" class="form-control mb-2" placeholder="Enter second value">
      <button class="btn btn-primary" @click="calculer">Calculer</button>
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
  
      const calculer = () => {
        result.value = value1.value - value2.value;
      };
  
      return { value1, value2, result, calculer };
    },
  };
  </script>
  