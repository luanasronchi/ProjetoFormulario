<template>
  <div class="container">
    <div class="row">
      <div class="col-6 bg-light">
        <span class="fs-4">ENTRADA DE DADOS</span>
        <hr />
        <form @submit.prevent="enviar($event)" @reset.prevent="resetar()">
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Nome:</label>
            <div class="col">
              <input type="text" class="form-control" v-model.lazy="form.nome" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">E-mail:</label>
            <div class="col">
              <input type="email" class="form-control" v-model.trim="form.email" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Senha:</label>
            <div class="col">
              <input type="password" class="form-control" v-model="form.senha" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Idade:</label>
            <div class="col">
              <input type="number" class="form-control" v-model.number="form.idade" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Gênero:</label>
            <div class="col">
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" value="Feminino" v-model="form.genero" />
                <label class="form-check-label"> Feminino </label>
              </div>
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" value="Masculino" v-model="form.genero" />
                <label class="form-check-label"> Masculino </label>
              </div>
            </div>
          </div>

          <div class="mb-3 row">
            <label class="col-3 col-form-label">Licença:</label>
            <div class="col">
              <div class="form-check form-switch">
                <input
                  class="form-check-input"
                  type="checkbox"
                  v-model="form.licenca"
                  true-value="SIM"
                  false-value="NÃO"
                />
                <label class="form-check-label">Li e aceito os termos</label>
              </div>
            </div>
          </div>

          <div class="mb-3 row">
            <label class="col-3 col-form-label">Interesses:</label>
            <div class="col">
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="JavaScript" v-model="form.interesses" />
                <label class="form-check-label"> JavaScript </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="VueJS" v-model="form.interesses" />
                <label class="form-check-label"> VueJS </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Angular" v-model="form.interesses" />
                <label class="form-check-label"> Angular </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="NodeJS" v-model="form.interesses" />
                <label class="form-check-label"> NodeJS </label>
              </div>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Telefone:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'(##) #####-####'" v-model="form.telefone" />
              <small class="text-muted">Formato: 00 00000-0000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CEP:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'#####-###'" v-model="form.cep" />
              <small class="text-muted">Formato: 00000-000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CPF:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'###.###.###-##'" v-model="form.cpf" />
              <small class="text-muted">Formato: 000.000.000-00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CNPJ:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'##.###.###/####-##'" v-model="form.cnpj" />
              <small class="text-muted">Formato: 00.000.000/0000-00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Cartão de Crédito:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'#### #### #### ####'" v-model="form.cartaoCredito" />
              <small class="text-muted">Formato: 0000 00 00 0000 0000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Placa Veículo:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'@@@-####'" v-model="form.placaVeiculo" />
              <small class="text-muted">Formato: AAA-0000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Placa Veículo Mercosul</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'@@@#@##'" v-model="form.placaVeiculoMercosul" />
              <small class="text-muted">Formato: AAA0A00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">RG:</label>
            <div class="col">
              <input type="text" class="form-control" v-maska="'AA-*'" v-model="form.rg" />
              <small class="text-muted">Formato: Sem padrão</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Data:</label>
            <div class="col">
              <input type="date" class="form-control" v-model="form.data" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Data/hora local:</label>
            <div class="col">
              <input type="datetime-local" class="form-control" v-model="form.dataHoraLocal" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Mês:</label>
            <div class="col">
              <input type="month" class="form-control" v-model="form.mes" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Semana:</label>
            <div class="col">
              <input type="week" class="form-control" v-model="form.semana" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Hora:</label>
            <div class="col">
              <input type="time" class="form-control" v-model="form.hora" />
            </div>
          </div>
          <div class="mb-3 row" >
            <label class="col-3 col-form-label" >Cor:</label>
            <div class="col">
              <input type="color" class="form-color" v-model="form.cor" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Valor limite:</label>
            <div class="col">
              <input type="range" class="form-range" min="0" max="100" step="1" v-model="form.alcance" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Escondido:</label>
            <div class="col">
              <input type="hidden" class="form-control" v-model="form.escondido"/>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Upload:</label>
            <div class="col">
              <input type="file" class="form-control" multiple @change="selecionarArquivos"/>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Descrição:</label>
            <div class="col">
              <textarea class="form-control" rows="3" v-model="form.descricao"></textarea>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Cursos:</label>
            <div class="col">
              <select class="form-select" v-model="form.curso">
                <option value="" disabled>Selecione um curso</option>
                <option v-for="curso in cursos" :key="curso.id" :value="curso.id">{{ curso.id }} - {{ curso.curso }}</option>
              </select>
            </div>
          </div>
          <hr />
          <div class="mb-3 row">
            <div class="col d-flex justify-content-between">
              <button class="btn btn-secondary" type="reset">Limpar</button>
              <button class="btn btn-success" type="button" @click="enviar($event)">Enviar (btn)</button>
              <button class="btn btn-success" type="submit">Enviar (submit)</button>
            </div>
          </div>
        </form>
      </div>

      <!-- SAÍDA -->
      <div class="col-6 text-white bg-secondary">
        <span class="fs-4">ESTADO DO OBJETO</span>
        <hr />
        <div class="mb-5 row">
          <spam>{{ form }}</spam>
        </div>

        <span class="fs-4">SAÍDA DE DADOS</span>
        <hr />
        <div class="mb-3 row">
          <spam>Nome: {{ form.nome }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>E-mail: {{ form.email }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Senha: {{ form.senha }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Idade: {{ form.idade }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Gênero: {{ form.genero }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Licença: {{ form.licenca }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Interesses:</spam>
          <ul>
            <li v-for="(interesse, index) in form.interesses" :key="index">{{ interesse }}</li>
          </ul>
        </div>
        <div class="mb-3 row">
          <spam>Telefone: {{ form.telefone }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>CEP: {{ form.cep }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>CPF: {{ form.cpf }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>CNPJ: {{ form.cnpj }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Cartão de Crédito: {{ form.cartaoCredito }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Placa Veículo: {{ form.placaVeiculo }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Placa Veículo Mercosul: {{ form.placaVeiculoMercosul }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>RG: {{ form.rg }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Data: {{ moment(form.data).format("DD/MM/YYYY") }} </spam>
        </div>
        <div class="mb-3 row">
          <spam>Data/hora local: {{ form.dataHoraLocal }}</spam>
          <ul>
            <li>{{ moment(form.dataHoraLocal).format("LL") }}</li>
            <li>{{ moment(form.dataHoraLocal).add(10, 'days').format('LL') }}</li>
            <li>{{ moment(form.dataHoraLocal).add(1, 'months').format('LL') }}</li>
            <li>{{ moment(form.dataHoraLocal).add(2, 'years').format('LL') }}</li>
          </ul>
        </div>
        <div class="mb-3 row">
          <spam>Mês: {{ form.mes }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Semana: {{ form.semana }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Hora: {{ form.hora }}</spam>
        </div>
        <div class="mb-3 row" :style="'color:'+form.cor+'!important'">
          <spam>Cor: {{ form.cor }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Valor limite: {{ form.alcance }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Escondido: {{ form.escondido }}</spam>
        </div>
        <div class="mb-3 row">
          <spam>Upload:</spam>
          <ul>
            <li v-for="(arquivo, index) in form.arquivos" :key="index">{{ arquivo.name }}</li>
          </ul>
        </div>
        <div class="mb-3 row">
          <spam>Descrição:</spam>
          <!-- <pre>{{ form.descricao }}</pre> -->
           <div style="white-space: pre;">{{ form.descricao }}</div>
        </div>
        <div class="mb-3 row">
          <spam>Descrição: {{ form.curso }}</spam>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { vMaska } from "maska/vue";
</script>

<script>
import moment from 'moment'
export default {
  name: "Formulario",
  data: () => ({
    cursos: [
    { id: 1, curso: 'Banco de dados Relacionais' },
    { id: 2, curso: 'Desenvolvimento WEB' },
    { id: 3, curso: 'Desenvolvimento BackEnd' },
    { id: 4, curso: 'Desenvolvimento Mobile' },
    ],
    form: {},
    formEstadoInicial: {
      nome: "Luana",
      email: "luana@gmail.com",
      senha: "12345",
      idade: "",
      licenca: false,
      interesses: ["JavaScript", "VueJS"],
      genero: "",
      telefone: "",
      cep: "",
      cpf: "",
      cnpj: "",
      cartaoCredito: "",
      placaVeiculo: "",
      placaVeiculoMercosul: "",
      rg: "",
      data: "",
      dataHoraLocal: "",
      mes: "",
      semana: "",
      hora: "",
      cor: '#ffffff',
      alcance: 5,
      escondido: 'Esse input está escondido',
      arquivos: {},
      descricao: '',
      curso: '',
      
    },
  }),
  created(){
    this.resetar()
  },
  methods: {
    moment,
    selecionarArquivos(event){
      this.form.arquivos = event.target.files
    },
    enviar(event){
      console.log(event)
      console.log(this.form)

      const formEnvio = Object.assign({}, this.form)
      console.log(formEnvio)
    },
    resetar(){
      this.form = Object.assign({}, this.formEstadoInicial)
    }
  }
};
</script>
