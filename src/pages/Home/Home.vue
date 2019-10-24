<template>
  <div class="home">
    <div class="container">
      <h1 class="main-title">Todo List</h1>
      <div class="create-todos">
        <vs-card class="card">
          <div class="inputs">
            <vs-input class="input-tarefa" label-placeholder="Título" v-model="tarefa.titulo"/>
            <vs-input class="input-tarefa" label-placeholder="Descrição" v-model="tarefa.descricao"/>
            <vs-button class="btn-add-tarefa" type="relief" @click="adicionaTarefa()">Add</vs-button>
          </div>
          <div class="radios-prioridade">
            <p>Prioridade:</p> 
            <vs-radio class="radio-prioridade" color="success" v-model="tarefa.prioridade" vs-value="isNormal" required>Normal</vs-radio>
            <vs-radio class="radio-prioridade" color="warning" v-model="tarefa.prioridade" vs-value="isMedio" required>Médio</vs-radio>
            <vs-radio class="radio-prioridade" color="danger" v-model="tarefa.prioridade" vs-value="isUrgente" required>Urgente</vs-radio>
          </div>
        </vs-card>
      </div>
      <div class="list-todos" v-for="(el, index) in listaTarefas" :key="index">
        <vs-card id="id_lista_todos" :class="el.prioridade">
          <div class="card-header" slot="header">
            <p>{{el.titulo}} #{{index + 1}}</p>
            <vs-button class="btn-del-tarefa" color="danger" type="relief" @click="deletaTarefa(index)">X</vs-button>
          </div>
          <vs-list>
            <vs-list-item :subtitle="el.descricao"></vs-list-item>
          </vs-list>
        </vs-card>
      </div>
    </div>
  </div>
  
</template>

<script>
export default {
  data () {
    return {
      tarefa: {
        titulo: '',
        descricao: '',
        prioridade: '',
      },
      listaTarefas: [],
    }
  },

  methods: {
    adicionaTarefa() {
      let titulo = this.tarefa.titulo;
      let descricao = this.tarefa.descricao;
      let prioridade = this.tarefa.prioridade;
      if (titulo == '' || descricao == '') {
        alert('Há campos em branco!');
      } else {
        this.listaTarefas.push({
          "titulo": titulo,
          "descricao": descricao,
          "prioridade": prioridade,
        });
        this.tarefa.titulo = ''; 
        this.tarefa.descricao = '';
        this.tarefa.prioridade = '';
      }
      
    },
    deletaTarefa(index) {
      this.listaTarefas.splice(index, 1);
    }
  }
}
</script>

<style scoped>
.main-title {
  padding-top: 60px;
  color: blue;
}
.home {
  height: 100vh;
}
.isNormal {
  background-color: rgba(23, 201, 100, 1);
  border-radius: 5px;
  color: white;
}

.isMedio {
  background-color: rgba(255, 130, 0, 1);
  border-radius: 5px;
  color: white;
}

.isUrgente {
  background-color: rgba(242, 19, 93, 1);
  border-radius: 5px;
  color: white;
}

.container {
  margin-right: 300px;
  margin-left: 300px;
}

.card {
  padding: 20px;
}
.card-header {
  font-size: 18px;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.create-todos {
  margin-top: 20px;
}
.radios-prioridade {
  display: flex;
  flex-direction: row;
  margin-top: 20px;
}
.radio-prioridade {
  margin-right: 10px;
}
.radios-prioridade p {
  margin-right: 5px;
  font-size: 14px;
}

.inputs {
  display: flex;
  justify-content: center;
}

.input-tarefa {
  margin-right: 10px;
  width: 100%;
}

.list-todos {
  margin-top: 20px;
}

.btn-add-tarefa {
  margin-top: 13px;
  width: 100px;
}

.btn-del-tarefa {
  width: 40px;
}
</style>