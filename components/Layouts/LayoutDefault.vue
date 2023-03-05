<template lang="pug">
    div
        Header
        main.container
            section.page-section
                <slot />
        Footer

</template>
<script>
import Header from '@/components/Layouts/Header'
import Footer from '@/components/Layouts/Footer.vue'

export default {
    name: 'LayoutDefault',
    components: {
        Header,
        Footer
    },
    methods: {
    },
    created() {
    }
}
</script>
