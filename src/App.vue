<script setup>
import { ref } from 'vue';

const isInputInvalid = ref(false);
const inputPasswordValue = ref('');

const checkInputValidity = () => {
    isInputInvalid.value = inputPasswordValue.value.length < 8
}
</script>

<template>
<div>
    <h2>
      Enter password
    </h2>
    <input 
      type="password" 
      :class="{
        'input-password': true, 
        'invalid-password': isInputInvalid
      }"
      v-model="inputPasswordValue" 
      @keyup="checkInputValidity" />
    <p v-if="isInputInvalid">
      Password should be at least 8 characters long!
    </p>
</div>
</template>

<style scoped>
.input-password {
    font-size: 16px;
    letter-spacing: 3px;
    padding: 4px 6px;
    outline: none;
    border: 1px solid #000;
}

.invalid-password {
  border: 1px solid red;
}
</style>