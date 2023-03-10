<template lang="pug">
    .mx-8.episodes(v-if="epsodes")
        h2.episodes__title Lista de episódios:

        table.episodes__table
            tr.episodes__tr
                th Código:
                th Nome:

            tr.episodes__tr(
                v-for="e in epsodes"
                v-bind:key="e.episode"
            )
                td {{ e.episode }}
                td
                    strong {{ e.name }}

</template>

<script>
    export default {
        name: 'Episodes',
        props: {
            epsodes: Array
        },
    }
</script>
