<template>
    <h1>Editar</h1>
</template>
<script>
export default {
    data() {
        return {
            contato: {}
        }
    },
    created() {
        alert(this.$route.params.id)
    }
}
</script>