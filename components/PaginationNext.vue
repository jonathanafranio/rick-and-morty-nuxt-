<template lang="pug">
    button.card-list__pagination-btn(
        @click="next"
    ) Exibir Mais Personagens
</template>

<script>
    export default {
        name: 'PaginationNext',
        props: {
            //next: String,
            //load: Boolean,
        },
        data() {
            return {}
        },
        methods: {
            next() {
                this.$emit('next-page')
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>
