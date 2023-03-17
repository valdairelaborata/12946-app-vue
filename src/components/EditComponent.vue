<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Editar Contato</h1>
            <form @submit.prevent="handleUpdateForm">
                <div class="form-group">
                    <label for="nome">Nome</label>
                    <input type="text" class="form-control" v-model="contato.nome" required>
                </div>
                <div class="form-group">
                    <label for="idade">Idade</label>
                    <input type="text" class="form-control" v-model="contato.idade" required @keypress="isNumber($event)"
                        maxlength="10">
                </div>
                <div class="form-group mt-3">
                    <button class="btn btn-success btn-block w-100" type="submit">Alterar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    data() {
        return {
            contato: {}
        }
    },
    created() {
        let apiURL = `http://localhost:3000/contatos/${this.$route.params.id}`;
        axios.get(apiURL).then((res) => {
            this.contato = res.data
        })
    },
    methods: {
        handleUpdateForm() {
            let apiURL = `http://localhost:3000/contatos/${this.$route.params.id}`;

            axios.put(apiURL, this.contato).then((res) => {
                console.log(res)
                this.$router.push('/view')
            }).catch(error => {
                console.log(error)  
            })
        }
    }
}
</script>