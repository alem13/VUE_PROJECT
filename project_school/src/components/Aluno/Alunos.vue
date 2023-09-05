<template>
  <div>
    <titulo text="Lista de Alunos"/>
    <div class="containerInput">
      <input type="text" placeholder="Nome aluno" v-model="nome" v-on:keyup.enter="addAluno()" >
      <button class="btn btnInput" @click="addAluno()"> Adicionar</button>
    </div>
      <br>
    <table>
      <thead v-if="alunos.length">
        <th>Mat.</th>
        <th>Nome</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="alunos.length">
        <tr v-for="(aluno, index) in alunos" :key="index">
          <td>{{ aluno.id }}</td>
          <td>{{ aluno.nome }}</td>
          <td>
            <button class="btn btn_Danger" @click="remover(aluno)"> Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-if="!alunos.length">
        <p>Nenhum aluno encontrado!!</p>
      </tfoot>
    </table>

  </div>
</template>

<script>

import Titulo from "../_shared/Titulo.vue"

export default {  
  components: {
    titulo: Titulo
  },
  data(){
    return{
      titulo:'Relação de Alunos', 
      nome:'',     
      alunos:[]
    }
  },
  created(){
    this.$axios
    .get('http://localhost:3000/alunos')
    // o restorno vem em formato de texto, precisa ser convertido para Json.
    .then(res => {
      this.alunos = res.data
    })
    .catch(error =>{
      console.log(error)
    })
  },
  props: {
  },
  methods: {

    addAluno() {
      let _aluno = {
        nome: this.nome,
        sobrenome:''
      }

      this.$axios
      .post('http://localhost:3000/alunos',_aluno)
      .then(res =>{
        this.alunos.push(res.data)
        this.nome = ""
      })
      
    },

    remover(aluno){

      this.$axios.
      delete(`http://localhost:3000/alunos/${aluno.id}`)
      .then(()=>{
        let indice = this.alunos.indexOf(aluno);
        this.alunos.splice(indice, 1)
      })

      
    }
  },
}
</script>

<style scoped>
input{
  font-size: 1.3em;
  padding: 10px 20px; 
  border-radius: 5px;
  border: 0;
  margin: 4px;
}

.btnInput{
  background-color: rgb(51, 151, 51);
}

.containerInput{
  display: flex;
  justify-content: center;
  align-items: center;
}
 
</style>
