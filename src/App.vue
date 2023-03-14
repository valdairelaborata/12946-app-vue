<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <h1>{{ titulo }}</h1>


  <ul>
    <li v-for="item in itens" :key="item.id">
      <p>
        {{ item.id }} - {{ item.nome }}
        <button v-if="item.finalizado">Excluir</button>
        <button v-else>Editar</button>
      </p>
    </li>
  </ul>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {

  data() {
    return {
      titulo: "Atividades",
      itens: [
        { id: 1, nome: 'Item 001', finalizado: false },
        { id: 2, nome: 'Item 002', finalizado: true },
        { id: 3, nome: 'Item 003', finalizado: true },
        { id: 4, nome: 'Item 004', finalizado: false }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
