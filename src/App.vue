<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <h1>{{ titulo }}</h1>


  <ul>
    <li v-for="item in itens" :key="item.id">
      <p v-if="!item.editando">
        {{ item.id }} - {{ item.nome }}
        <button v-if="item.finalizado" @click="excluir(item)">Excluir</button>
        <button v-else @click="alterar(item)">Editar</button>
      </p>
      <div v-else>
        {{ item.nome }}
        <input v-model="item.nome">
        <button @click="confirmar(item)">Confirmar</button>
      </div>
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
        { id: 1, nome: 'Item 001', finalizado: false, editando: false },
        { id: 2, nome: 'Item 002', finalizado: true, editando: false },
        { id: 3, nome: 'Item 003', finalizado: true, editando: false },
        { id: 4, nome: 'Item 004', finalizado: false, editando: false }
      ]
    }
  },
  methods: {
    excluir(item) {

      if (confirm('Deseja excluir o item ' + item.nome + '?')) {
        this.itens = this.itens.filter(x => x.id != item.id)
      }

    },
    alterar(item) {
      let registro = this.itens.find((x) => {
        return x.id === item.id
      })

      registro.editando = true
    },
    confirmar(item) {
      let registro = this.itens.find((x) => {
        return x.id === item.id
      })
      registro.editando = false
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
