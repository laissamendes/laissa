<script setup>
import { ref, computed } from 'vue'

const nome = ref("")
const email = ref("")
const senha = ref("")
const confirmacao_senha = ref("")
const nascimento = ref("")
const endereco = ref("")
const cidade = ref("")
const estado = ref("")
const hobbies = ref("")
const ling_programacao = ref("")
const biografia = ref("")
</script>

<template>
  <div class="editor">
<div class="nome">
<input type="text" v-model="nome" placeholder="Digite seu nome...">
</div>
<div class="email">
  <input type="text" v-model="email" placeholder="Digite seu e-mail...">
</div>
<div class="senha">
  <input type="passaword" v-model="senha" placeholder="Digite sua senha...">
</div>
<div class="confirmacao_senha">
  <input type="passaword" v-model="confirmacao_senha" placeholder="Confirme sua senha...">
</div>
<div class="nascimento">
  <label for="nascimento">Insira sua data de Nascimento:</label>
  <input type="date" v-model="nascimento">
</div>
<div class="endereco">

</div>
<div class="cidade">

</div>
<div class="estado">

</div>
<div class="hobies">

</div>
<div class="ling_prog">

</div>
<div class="biografia">

</div>
  </div>
</template>

<style scoped>

</style>
