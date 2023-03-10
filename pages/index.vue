<template lang="pug">
    LayoutDefault
        SearchForm

        ListCharacter(title="Lista de personagens")

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
}
</script>
