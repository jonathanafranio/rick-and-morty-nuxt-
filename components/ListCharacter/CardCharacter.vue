<template lang="pug">
    article.card-post.mx-4.md-6.sm-6(:id="id_character")
        .card-post__container
            figure.card-post__figure
                img(:src="thumb" :alt="title")

            .card-post__text
                span.card-post__categ {{ species }}
                h3.card-post__title {{ title }}

            a.card-post__link(
                :href="`/personagem/${this.id_character}`"
            ) Ver detalhes


</template>
<script>
export default {
    props: {
        id_character: Number,
        title: String,
        species: String,
        thumb: String,

    },
    data() {
    },
    methods: {
    },
}
</script>
