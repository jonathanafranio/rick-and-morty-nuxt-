<template lang="pug">
    LayoutDefault
        Preload(v-if="loading")

        .character(v-else)
            h1.page-section__title Personagem: {{ title }}

            CharacterInfo(
                :title="title"
                :image="image"
                :status="status"
                :species="species"
                :gender="gender"
                :origin="origin"
                :location="location_home"
            )

            Episodes(:epsodes="episode")



</template>

<script>
    import LayoutDefault from '@/components/Layouts/LayoutDefault'
    import Preload from '@/components/Preload'
    import CharacterInfo from '@/components/CharacterInfo'
    import Episodes from '@/components/Episodes'

    export default {
        name: 'Personagem',
        components: {
            LayoutDefault,
            Preload,
            CharacterInfo,
            Episodes
        },
        data(){
            return {
                loading: true,
                id: this.$route.params.personagem,
                title: '',
                image: '',
                status: '',
                species: '',
                gender: '',
                origin: '',
                location_home: '',
                episode: []
            }
        },
        methods: {
            get_character() {
                //fetch(`https://rickandmortyapi.com/api/character/${this.id}`)

                const variables = {}
                const query = `{\n
                    character(id: ${this.$route.params.personagem}) {\n
                        id\n
                        name\n
                        image\n
                        status\n
                        species\n
                        gender\n
                        origin {\n
                            name\n
                        }\n
                        location {\n
                            name\n
                        }\n
                        episode {\n
                            name\n
                            episode\n
                        }\n
                    }\n
                }`

                const option = {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({ query: query, variables: variables })
                }

                fetch(`https://rickandmortyapi.com/graphql`, option)
                    .then(r => r.json())
                    .then(res => {
                        const r = res.data.character

                        this.title = r.name
                        this.image = r.image
                        this.status = r.status
                        this.species = r.species
                        this.gender = r.gender
                        this.origin = r.origin.name
                        this.location_home = r.location.name
                        this.episode = r.episode
                        this.loading = false
                    })
            }
        },

        created() {
            this.get_character()
        }
    }
</script>
