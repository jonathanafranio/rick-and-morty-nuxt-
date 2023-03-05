<template lang="pug">
    .mx-8.episodes
        h2.episodes__title Lista de episódios:

        table.episodes__table(v-if="episodios")
            tr.episodes__tr
                th Código:
                th Nome:

            tr.episodes__tr(
                v-for="e in episodios"
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
        data() {
            return {
                episodios: []
            }
        },
        methods: {
            get_epsode(url){
                if(!url) return

                fetch(url)
                    .then(r => r.json())
                    .then(r => {
                        const { name, episode } = r
                        this.episodios.push({ name, episode })
                    })
                    .catch(e => console.log('erro', e))
            },
            for_epsodes(){
                if(! this.epsodes) return;

                this.epsodes.forEach(e => {
                    this.get_epsode(e)
                });
            }
        },
        created() {
            this.for_epsodes();

        },
    }
</script>
