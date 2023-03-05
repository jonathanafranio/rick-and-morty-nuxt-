<template lang="pug">
    LayoutDefault
        SearchForm

        Preload(v-if="loading")
        ListCharacter(:characters="characters" v-else)



</template>

<script>
import LayoutDefault from '@/components/Layouts/LayoutDefault'
import SearchForm from '@/components/SearchForm'
import Preload from '@/components/Preload'
import ListCharacter from '@/components/ListCharacter/ListCharacter'

export default {
    name: 'IndexPage',
    components: {
        LayoutDefault,
        SearchForm,
        Preload,
        ListCharacter
    },
    data(){
        return {
            characters: [],
            sccp: 'VAI CORINTHIANS',
            pagination: {
                next: 'https://rickandmortyapi.com/api/character',
                prev: null
            },
            loading: true,
        }
    },
    methods: {
        get_character(url){
            if(!url) return
            fetch(url)
                .then(r => r.json())
                .then(res => {
                    const { results, info } = res
                    this.pagination.next = info.next
                    this.pagination.prev = info.prev
                    this.characters.push(results)
                    //this.characters = results
                    this.loading = false
                })
                .catch(e => console.log("deu ruim a promisse", e))
        }
    },
    created() {
        this.get_character(this.pagination.next)
    }
}
</script>
