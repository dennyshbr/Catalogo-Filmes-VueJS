<template>
  <div>

    <titulo texto="Filmes" />

    <input type="text" placeholder="Nome do Filme" v-model="nome">
    <button class="btn btn-input" @click="adicionarFilme()">Adicionar</button>

    <table>
      <thead>
        <th>Id</th>
        <th>Titulo</th>
        <th>Ano Lançamento</th>
        <th>Duração</th>
        <th>Classificação</th>
        <th>Opções</th>
      </thead>
      <tbody v-if="filmes.length">
        <tr v-for="(filme, index) in filmes" :key="index">
          <td>{{ filme.id }}</td>
          <td>{{ filme.titulo }}</td>
          <td>{{ filme.anoLancamento }}</td>
          <td>{{ filme.duracao }}</td>
          <td>{{ filme.classificacao }}</td>
          <td>
            <button class="btn btn-danger" @click="removerFilme(filme)">Remover</button>
          </td>
        </tr>
      </tbody>
      <tfoot v-else>
          Nenhum aluno encontrado
      </tfoot>
    </table>
  </div>
</template>

<script>

import Titulo from '../share/Titulo.vue';

export default {
  components:{
    Titulo
  },
  data() {
    return {
      titulo: 'Filme',
      nome: '',
      filmes: []
    }
  },
  created() {

    this.$http
      .get('http://localhost:3000/filmes')
      .then(res => res.json())
      .then(retorno => this.filmes = retorno);
  },
  props: {
    
  },
  methods: {
    adicionarFilme() {

      let filme = {
        titulo: this.nome,
        anoLancamento: "",
        duracao: 0,
        classificacao: ""
      };

      this.$http
      .post('http://localhost:3000/filmes', filme)
      .then(res => res.json())
      .then(filmeRetornado => {
        this.filmes.push(filmeRetornado);
        this.nome = '';
      });

      
    },
    removerFilme(filme){

      this.$http
      .delete(`http://localhost:3000/filmes/${filme.id}`)
      .then(() => {
        let indice = this.filmes.indexOf(filme);
        this.filmes.splice(indice, 1);
      });
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  
  input{
    border: 0;
    padding:20px;
    font-size: 1.3em;
    color: #687f7f;
    display:inline;
  }

  .btn-input{
    border:0;
    padding:20px;
    font-size: 1.3em;
    background-color: rgb(116,115,115);
  }

  .btn-input:hover{
    margin: 0px;
  }
</style>
