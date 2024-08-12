<template>
  <div class="calculator-container">
    <form @submit.prevent="calculate">
      <div class="form-group">
        <label for="number1">Nombre 1</label>
        <input
          type="number"
          id="number1"
          v-model.number="numbers[0]"
          class="form-control"
          placeholder="Entrez le premier nombre"
          required
        />
      </div>
      <div class="form-group">
        <label for="number2">Nombre 2</label>
        <input
          type="number"
          id="number2"
          v-model.number="numbers[1]"
          class="form-control"
          placeholder="Entrez le deuxième nombre"
          required
        />
      </div>
      <div class="form-group">
        <label for="number3">Nombre 3 (optionnel)</label>
        <input
          type="number"
          id="number3"
          v-model.number="numbers[2]"
          class="form-control"
          placeholder="Entrez le troisième nombre"
        />
      </div>
      <div class="operation-group">
        <label class="operation-label">Opération</label>
        <div class="operations">
          <button
            type="button"
            @click="operation = 'add'"
            :class="{ 'active': operation === 'add' }"
            class="operation-btn"
          >
            Addition
          </button>
          <button
            type="button"
            @click="operation = 'subtract'"
            :class="{ 'active': operation === 'subtract' }"
            class="operation-btn"
          >
            Soustraction
          </button>
          <button
            type="button"
            @click="operation = 'multiply'"
            :class="{ 'active': operation === 'multiply' }"
            class="operation-btn"
          >
            Multiplication
          </button>
          <button
            type="button"
            @click="operation = 'divide'"
            :class="{ 'active': operation === 'divide' }"
            class="operation-btn"
          >
            Division
          </button>
        </div>
      </div>
      <button type="submit" class="btn-primary">Calculer</button>
    </form>
    <div v-if="result !== null" class="result-container">
      <h2 class="result-title">Résultat</h2>
      <p class="result">{{ formattedResult }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const numbers = ref([0, 0, 0]);
const operation = ref('add');
const result = ref(null);

const calculate = () => {
  const [num1, num2, num3] = numbers.value;
  switch (operation.value) {
    case 'add':
      result.value = num1 + num2 + (num3 || 0);
      break;
    case 'subtract':
      result.value = num1 - num2 - (num3 || 0);
      break;
    case 'multiply':
      result.value = num1 * num2 * (num3 || 1);
      break;
    case 'divide':
      result.value = num2 !== 0 ? num1 / num2 / (num3 || 1) : 'Erreur (division par zéro)';
      break;
  }
};

const formattedResult = computed(() => {
  return typeof result.value === 'number'
    ? result.value.toLocaleString('fr-FR') /* Affichage du nombre sans symbole monétaire */
    : result.value;
});
</script>

<style scoped>
.calculator-container {
  padding: 20px;
  border: 2px solid #00bcd4; /* Bordure turquoise éclatante */
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  background-color: #ffffff; /* Fond blanc pour faire ressortir les couleurs */
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  color: #333; /* Texte sombre pour une bonne lisibilité */
}

.form-control {
  border: 1px solid #00bcd4; /* Bordure turquoise éclatante */
  border-radius: 5px;
  padding: 10px;
  background-color: #f0f0f0; /* Fond gris clair pour les champs de saisie */
}

.operation-group {
  margin-bottom: 20px;
}

.operation-label {
  display: block;
  margin-bottom: 10px;
  font-weight: bold;
  font-size: 1.2rem;
  color: #00bcd4; /* Couleur turquoise éclatante pour le label */
}

.operations {
  display: flex;
  justify-content: space-between;
}

.operation-btn {
  background-color: #ffffff; /* Fond blanc pour les boutons d'opération */
  border: 2px solid #00bcd4; /* Bordure turquoise éclatante */
  border-radius: 8px; /* Bordures arrondies pour les boutons */
  padding: 10px 20px;
  font-size: 1rem;
  font-weight: bold;
  color: #00bcd4; /* Texte turquoise éclatant */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: background-color 0.3s, border-color 0.3s, color 0.3s;
}

.operation-btn:hover {
  background-color: #00bcd4; /* Fond turquoise au survol */
  color: #ffffff; /* Texte blanc au survol */
}

.operation-btn.active {
  background-color: #00acc1; /* Fond turquoise plus foncé pour le bouton actif */
  color: #ffffff; /* Texte blanc pour le bouton actif */
}

.btn-primary {
  background-color: #4caf50; /* Couleur verte éclatante pour le bouton principal */
  border-color: #4caf50;
  color: #ffffff; /* Texte blanc */
}

.btn-primary:hover {
  background-color: #388e3c; /* Couleur verte plus sombre au survol */
}

.result-container {
  margin-top: 20px;
  padding: 10px;
  border: 2px solid #00bcd4; /* Bordure turquoise éclatante */
  border-radius: 5px;
  background-color: #f0f0f0; /* Fond gris clair pour la zone de résultat */
}

.result-title {
  font-size: 1.5rem;
  color: #00bcd4; /* Couleur turquoise éclatante pour le titre du résultat */
  margin-bottom: 10px;
}

.result {
  font-size: 2rem;
  color: #333;
  font-weight: bold;
}
</style>
