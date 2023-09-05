<template>
  <div id="app">
    <Alunos/> 
  </div>
</template>

<script>

import Alunos from './components/Aluno/Alunos.vue'

export default {
  name: 'app',
  components: {
    Alunos
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body{
  background-color: #eee ;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-content: center;
}

body, html{
  margin: 0;
  padding: 0;
  height: 100%;
}

#app{

}

table{
    margin: 0px;
    padding: 0px;
    list-style-type: none;
    width: 100%;
  }

  table thead th{
    background-color:rgb(147, 92, 173) !important;
    font-size: 1.2em;
    padding: 10px 0px;
    text-align: center !important;
  }

  table tr td{
    padding: 20px;
    font-size: 1.3em;
    background-color:rgb(206, 175, 236);
    margin-bottom: 2px;
    color: rgb(27, 5, 29);
  }
  
  .colPequeno{
    width: 5%;
  }

  .btn_Danger{
    background-color: #fa4430;
  }

  .btn { 
  color: white; /* Cor do texto (branco, por exemplo) */
  border: 1px solid black; /* Borda 1px sólida preta */
  border-radius: 5px; /* Bordas arredondadas */
  border-bottom: 3px solid black;
  padding: 10px 20px; /* Espaçamento interno (ajuste conforme necessário) */
  text-decoration: none; /* Remover sublinhado padrão (se for um link) */
  cursor: pointer; /* Cursor de mão ao passar o mouse */
}

/* Estilos adicionais ao passar o mouse (opcional) */
.btn:hover {
  text-shadow: 1px 1px 1px black;
  margin-top: 3px;
  border-bottom: 1px solid black;
}

</style>
