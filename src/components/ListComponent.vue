<template>
    <div class="justify-content-center">
        <h1>Lista de Contatos</h1>
        <div class="row">
            <div class="col-md-12">
                <div class="table-responsive">
                    <table class="table table-striped">
                        <thead class="table-dark">
                            <tr>
                                <th>Nome</th>
                                <th>Idade</th>
                                <th class="text-end">Ações</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="contato in contatos" :key="contato.id">
                                <td>{{ contato.nome }}</td>
                                <td>{{ contato.idade }}</td>
                                <td class="text-end">
                                    <router-link :to="{ name: 'edit', params: { id: contato.id } }"
                                        class="btn btn-success me-2">
                                        Editar
                                    </router-link>

                                    <button @click.prevent="excluir(contato)" class="btn btn-danger">Excluir </button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>
<script>


import axios from "axios"

export default {
    data() {
        return {
            contatos: []
        }
    },
    created() {
        let apiURL = 'http://localhost:3000/contatos'
        axios.get(apiURL).then((res) => {
            this.contatos = res.data
        }).catch(error => {
            console.log(error)
        })
    },
    methods: {
        excluir(contato) {
            alert(JSON.stringify(contato))
        }
    }


}

</script>