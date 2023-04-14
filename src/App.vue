<script setup>
import { ref} from 'vue'

const nome = ref('')
const dtNascimento = ref('')
const email = ref('')
const senha = ref('')
const confirmacao_senha = ref('')
const endereco_rua = ref('')
const endereco_numero = ref('')
const endereco_bairro = ref('')
const cidade = ref('')
const estado = ref('')
const hobbies = ref('')
const ling_programacao = ref('')
const biografia = ref('')
const imagem = ref('')
const enviar = ref(false)
const msgErro = ref('')

function confirmacao() {
  if (senha.value === confirmacao_senha.value) {
    msgErro.value = "";
    return true;
  } else {
    msgErro.value = "Senha e Confirmação de Senha não conferem!"
    return false
  }
}

function handleFileUpload(e) {
  const target = e.target
  if (target && target.files) {
    const file = target.files[0]
    console.log(file)
    imagem.value = URL.createObjectURL(file)
  }
}

</script>

<template>
  <div id="editor">
    <form @submit.prevent="enviar = confirmacao()">
      <h1>Edição de Perfil</h1>
      <h3>Informações pessoais</h3>
      <div class="nome">
        <input
          type="text"
          v-model="nome"
          v-on:keypress="enviar = false"
          placeholder="Digite seu nome..."
          required
        />
      </div>
      <div class="nascimento">
        <h4>Insira sua data de Nascimento:</h4>
        <input type="date" v-model="dtNascimento" v-on:keypress="enviar = false" required />
      </div>
      <div class="email">
        <input
          type="email"
          v-model="email"
          v-on:keypress="enviar = false"
          placeholder="Digite seu e-mail..."
          required
        />
      </div>
      <hr />
      <h3>Informações de senha</h3>
      <div class="senha">
        <input
          type="password"
          v-model="senha"
          v-on:keypress="enviar = false"
          placeholder="Digite sua senha..."
          required
        />
      </div>
      <div class="confirmacao_senha">
        <input
          type="password"
          v-model="confirmacao_senha"
          v-on:keypress="enviar = false"
          placeholder="Confirme sua senha..."
          required
        />
      </div>
      <hr />
      <h3>Informações de endereço</h3>
      <div class="endereco_rua">
        <input
          type="text"
          v-model="endereco_rua"
          v-on:keypress="enviar = false"
          placeholder="Digite sua rua..."
        />
      </div>
      <div class="endereco_numero">
        <input
          type="number"
          v-model="endereco_numero"
          v-on:keypress="enviar = false"
          min="1"
          placeholder="Número da sua casa..."
        />
      </div>
      <div class="endereco_bairro">
        <input
          type="text"
          v-model="endereco_bairro"
          v-on:keypress="enviar = false"
          placeholder="Digite seu bairro..."
        />
      </div>
      <div class="cidade">
        <input
          type="text"
          v-model="cidade"
          v-on:keypress="enviar = false"
          placeholder="Digite sua cidade..."
        />
      </div>
      <div class="estado">
        <h4>Insira seu estado:</h4>
        <select v-model="estado" v-on:keypress="enviar = false">
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
      <hr />
      <div class="hobies">
        <h4>Insira seus Hobbies:</h4>
        <textarea v-model="hobbies" v-on:keypress="enviar = false"></textarea>
      </div>
      <div class="ling_prog">
        <h4>Diga quais são as suas linguagens de programação:</h4>
        <textarea v-model="ling_programacao" v-on:keypress="enviar = false"></textarea>
      </div>
      <div class="biografia">
        <h4>Insira uma Biografia:</h4>
        <textarea v-model="biografia" v-on:keypress="enviar = false"></textarea>
      </div>
      <div>
        <h3>Escolha sua nova foto de perfil</h3>
        
        <input
          type="file"
          id="imagem"
          @change="handleFileUpload($event)"
        />      
      </div>
      <button type="submit">Enviar</button>
    </form>
    <div id="msgErro"><p>{{ msgErro }}</p></div>
  </div>

  <div v-if="enviar" id="editado">
    <h1>Perfil Atualizado:</h1>
    <div class="img_atual">
      <img :src="imagem" alt="" />
    </div>
    <div class="nome_atual">
      <p>{{ nome }}</p>
    </div>
    <div class="dt_nascimento-atualizado">
      <p>{{ dtNascimento.substr(8,2)+"/"+dtNascimento.substr(5,2)+"/"+dtNascimento.substr(0,4) }}</p>
    </div>
    <div class="email-atual">
      <p>{{ email }}</p>
    </div>
    <div class="senha-atual"></div>
    <div class="endereco-atual" v-if="endereco_rua!=''.trim() && endereco_numero!=''.trim() && endereco_bairro!=''.trim() && cidade!=''.trim() && estado!=''.trim()">
      <p>
        Endereço: {{ endereco_rua }}, {{ endereco_numero }},{{ endereco_bairro }}, {{ cidade }},
        {{ estado }}
      </p>
    </div>
    <div class="hoobie_atualizado" v-if="hobbies!=''.trim()">Hoobie(s): {{ hobbies }}</div>
    <div class="ling_atualizada" v-if="ling_programacao!=''.trim()">Linguagem(s) de Programação: {{ ling_programacao }}</div>
    <div class="bio-atualizada" v-if="biografia!=''.trim()">Biografia: {{ biografia }}</div>
  </div>
</template>

<style scoped>
div {
  margin: 5px;
}
#editado {
  background-color: rgba(169, 169, 169, 0.842);
  border-radius: 5px;
  border-color: rgb(70, 69, 69);
  border-style: solid;
  color: white;
  padding: 10px;
  box-shadow: 5px 5px 20px black;
  width: 500px;
  font-size: 20px;
}
#editor {
  background-color: rgba(169, 169, 169, 0.842);
  border-radius: 5px;
  border-color: rgb(70, 69, 69);
  border-style: solid;
  color: white;
  padding: 10px;
  box-shadow: 5px 5px 20px black;
}
.img_atual {
  width: '80%';
  display: flex;
  justify-content: center;
}

.img_atual img {
  width: 200px;
  height: 200px;
  border-radius: 50%;
}
#msgErro{
  color: black;
  background-color: rgba(255, 255, 255, 0.692);
  border-radius: 5px;
  text-align: center;
  box-shadow: 2px 2px 10px black;
}
button{
  border-color: white;
  color: white;
  background-color: rgb(109, 109, 109);
}
button:hover{
  box-shadow: 1px 1px 5px black;
  background-color: rgb(82, 81, 81);
}

</style>
