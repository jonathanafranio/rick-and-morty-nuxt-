<template lang="pug">
    div
        Header
        main.container
            section.page-section
                <slot />

</template>
<script>
import Header from '@/components/Layouts/Header'

export default {
    name: 'LayoutDefault',
    components: {
        Header
    },
    methods: {
    },
    created() {
    }
}
</script>
