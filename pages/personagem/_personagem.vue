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
                fetch(`https://rickandmortyapi.com/api/character/${this.id}`)
                    .then(r => r.json())
                    .then( r => {
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
