<template>
  <div>
    <div class="input-container">
      <input type="text" v-model="inputText" @input="checkInput" :class="{ 'input-error': inputError }">
      <span v-if="inputError" class="input-error">{{ errorMessage }}</span>
    </div>
    <p v-if="inputText.length > 0">Length of Input Text: {{ inputText.length }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const inputText = ref('');
const inputError = ref(false);
const errorMessage = ref('');

function checkInput() {
  if (inputText.value.length > 10) {
    inputError.value = true;
    errorMessage.value = 'Input text is too long!';
  } else {
    inputError.value = false;
    errorMessage.value = '';
  }
}
</script>

<style>
.input-container {
  margin-bottom: 10px;
}

.input-error {
  color: red;
}

.input-error + input {
  border-color: red;
}
</style>
