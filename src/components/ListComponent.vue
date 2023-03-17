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
                            <tr v-for="contato in Contatos" :key="contato.id">
                                <td>{{ contato.nome }}</td>
                                <td>{{ contato.idade }}</td>
                                <td class="text-end">
                                    <router-link :to="{ name: 'edit', params: { id: contato.id } }"
                                        class="btn btn-success me-2">
                                        Editar
                                    </router-link>
                                    <button @click.prevent="excluir(contato.id)" class="btn btn-danger">
                                        Excluir
                                    </button>
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
import axios from "axios";

export default {
    data() {
        return {
            Contatos: []
        }
    },
    created() {
        let apiURL = 'http://localhost:3000/Contatos';
        axios.get(apiURL).then(res => {
            this.Contatos = res.data
        }).catch(error => {
            console.log(error)
        })
    },
    methods: {
        excluir(id) {
            let apiURL = `http://localhost:3000/Contatos/${id}`;
            let indexOfArrayItem = this.Contatos.findIndex(i => i.id === id);

            if (window.confirm("Confirma excluir o registro?")) {
                axios.delete(apiURL).then(() => {
                    this.Contatos.splice(indexOfArrayItem, 1)
                }).catch(error => {
                    console.log(error)
                })
            }
        }
    }
}
</script>