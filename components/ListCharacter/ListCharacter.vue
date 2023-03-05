<template lang="pug">
    .character-list(v-if="characters")
        .character-list__page(
            v-for="(page, i) in characters"
            v-bind:key="i"
            :id="`page-${i}`"
        )
            CardCharacter(
                v-for="character in page"
                v-bind:key="character.id"
                :id_character="character.id"
                :title="character.name"
                :species="character.species"
                :thumb="character.image"
            )

        PaginationNext(
            v-if="pagination.next && !loading"
            :load="loading"
            v-on:next-page="next_page"
        )

        Preload(v-if="loading")

</template>

<script>
import CardCharacter from './CardCharacter'
import PaginationNext from '../PaginationNext'
import Preload from '../Preload'

    export default {
        name: 'ListCharacter',
        components: {
            CardCharacter,
            PaginationNext,
            Preload
        },
        props: {
            request_url: {
                type: String,
                default() { return 'https://rickandmortyapi.com/api/character' }
            }
        },
        data(){
            return {
                characters: [],
                pagination: {
                    next: null,
                    prev: null
                },
                loading: true,
            }
        },
        methods: {
            get_character(url){
                if(!url) return
                console.log({ url })
                fetch(url)
                    .then(r => r.json())
                    .then(res => {
                        const { results, info } = res
                        this.pagination.next = info.next
                        this.pagination.prev = info.prev
                        this.characters.push(results)
                        this.loading = false

                    })
                    .catch(e => {
                        console.log("deu ruim a promisse", e)
                        this.loading = false
                    })
            },
            next_page() {
                if(!this.pagination.next) return
                this.loading = true

                this.get_character(this.pagination.next)
            }
        },
        created() {
            this.get_character(this.request_url)
        },
    }
</script>

