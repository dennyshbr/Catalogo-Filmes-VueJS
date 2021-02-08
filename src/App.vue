<template>
  <div id="app">
    
    <Filmes />
  </div>
</template>

<script>
import Filmes from './components/Filme/Filmes.vue'

export default {
  name: 'App',
  components: {
    Filmes
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:400, 700");

body{
  background-color: #eee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  justify-items: center;
}

body, html{
  margin: 0;
  height: 100%;
}

#app{

}

.btn-danger{
  background-color: #fa4430;
}

.btn{
  padding: 10px 20px;
  cursor: pointer;
  border: 1px solid #000;
  color:white;
  font-weight: bold;
  border-radius: 5px;
  border-bottom: 3px solid black;
}

.btn:hover{
  border-bottom: 1px solid black;
  margin-top: 2px;
}

table{
  margin: 0;
  padding: 0;
  list-style-type: none;
  width: 100%;
}

table tr td{
  padding: 20px;
  font-size: 1.3em;
  background-color: #e0edf4;
  margin-bottom: 2px;
  color: #3e5252;
}

table thead th{
  background-color: rgb(184, 208, 216) !important;
  font-size: 1.2em;
  padding: 10px 10px;
  text-align: center !important;
}

.coluna-pequena{
  width: 5%;
}
</style>
