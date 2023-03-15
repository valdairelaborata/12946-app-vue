<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Novo Contato</h1>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label>Nome</label>
                    <input type="text" class="form-control" v-model="contato.nome" required>
                </div>
                <div class="form-group">
                    <label for="idade">Idade</label>
                    <input type="text" class="form-control" v-model="contato.idade" required maxlength="10">
                </div>
                <div class="form-group mt-3">
                    <button class="btn btn-success btn-block w-100" type="submit">Criar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            contato: {
                nome: '',
                idade: ''
            }
        }
    },
    methods: {
        handleSubmitForm() {
            alert(JSON.stringify(this.contato))
        }

    }
}
</script>