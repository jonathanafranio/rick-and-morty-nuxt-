<template lang="pug">
    LayoutDefault
        SearchForm

        ListCharacter(:title="title" :page="page" :page_url="prefix_url" search="")

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
            title: `Lista de personagens - página: ${this.$route.params.p}`,
            page: this.$route.params.p
        }
    },
    computed: {
        prefix_url(){
            let url = null;
            if (process.browser) {
                url = location.origin
            }
            return url
        }
    }
}
</script>
