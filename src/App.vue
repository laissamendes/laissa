<script setup>
import { ref, computed } from 'vue'

const nome = ref("")
const email = ref("")
const senha = ref("")
const confirmacao_senha = ref("")
const nascimento = ref("")
const endereco_rua = ref("")
const endereco_numero = ref("")
const endereco_bairro = ref("")
const cidade = ref("")
const estado = ref("")
const hobbies = ref("")
const ling_programacao = ref("")
const biografia = ref("")
</script>

<template>
  <div id="editor">
    <form @submit.prevent="enviar">
      <h1>Edição de Perfil</h1>
      <h3>Informações pessoais</h3>
<div class="nome">
<input type="text" v-model="nome" placeholder="Digite seu nome...">
</div>
<div class="nascimento">
  <h4>Insira sua data de Nascimento:</h4>
  <input type="date" v-model="nascimento">
</div>
<div class="email">
  <input type="email" v-model="email" placeholder="Digite seu e-mail...">
</div>
<hr>
<h3>Informações de senha</h3>
<div class="senha">
  <input type="passaword" v-model="senha" placeholder="Digite sua senha...">
</div>
<div class="confirmacao_senha">
  <input type="passaword" v-model="confirmacao_senha" placeholder="Confirme sua senha...">
</div>
<hr>
<h3>Informações de endereço</h3>
<div class="endereco_rua">
  <input type="text" v-model="endereco_rua" placeholder="Digite sua rua...">
</div>
<div class="endereco_numero">
  <input type="number" v-model="endereco_numero" min="1" placeholder="Digite o número da sua casa...">
</div>
<div class="endereco_bairro">
  <input type="text" v-model="endereco_bairro" placeholder="Digite seu bairro...">
</div>
<div class="cidade">
  <input type="text" v-model="cidade" placeholder="Digite sua cidade...">
</div>
<div class="estado">
  <h4>Insira seu estado:</h4>
<select v-model="estado">
<option value="AC">Acre</option>
<option value="AL">Alagoas</option>
<option value="AP">Amapá</option>
<option value="AM">Amazonas</option>
<option value="BA">Bahia</option>
<option value="CE">Ceará</option>
<option value="ES">Espírito Santo</option>
<option value="GO">Goiás</option>
<option value="MA">Maranhão</option>
<option value="MT">Mato Grosso</option>
<option value="MS">Mato Grosso do Sul</option>
<option value="MG">Minas Gerais</option>
<option value="PA">Pará</option>
<option value="PB">Paraíba</option>
<option value="PR">Paraná</option>
<option value="PE">Pernambuco</option>
<option value="PI">Piauí</option>
<option value="RJ">Rio de Janeiro</option>
<option value="RN">Rio Grande do Norte</option>
<option value="RS">Rio Grande do Sul</option>
<option value="RO">Rondônia</option>
<option value="RR">Roraima</option>
<option value="SC">Santa Catarina</option>
<option value="SP">São Paulo</option>
<option value="SE">Sergipe</option>
<option value="TO">Tocantins</option>
</select>
</div>
<hr>
<div class="hobies">
  <h4>Insira seus Hobbies:</h4>
  <textarea v-model="hobbies"></textarea>
</div>
<div class="ling_prog">
  <h4>Diga quais são as suas linguagens de programação:</h4>
  <textarea v-model="ling_programacao"></textarea>
</div>
<div class="biografia">
  <h4>Insira uma Biografia:</h4>
  <textarea v-model="biografia"></textarea>
</div>
<button type="submit">Enviar</button>
</form>
  </div>
</template>

<style scoped>
div{
  margin:5px;
}
#editor{
  background-color: rgba(169, 169, 169, 0.842);
  border-radius: 5px;
  border-color: rgb(70, 69, 69);
  border-style: solid;
  color: white;
}
</style>
