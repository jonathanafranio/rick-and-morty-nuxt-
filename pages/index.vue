<template lang="pug">
    LayoutDefault
        SearchForm

        ListCharacter(title="Lista de personagens" :request_url="request_url")





</template>

<script>
import LayoutDefault from '@/components/Layouts/LayoutDefault'
import SearchForm from '@/components/SearchForm'

import ListCharacter from '@/components/ListCharacter/ListCharacter'

export default {
    name: 'IndexPage',
    components: {
        LayoutDefault,
        SearchForm,
        ListCharacter
    },
    data(){
        return {
            request_url: 'https://rickandmortyapi.com/api/character'
        }
    },
    methods: {
    },
}
</script>
