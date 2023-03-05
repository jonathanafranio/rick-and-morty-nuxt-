<template lang="pug">
    header.header
        div.container
            a.header__logo(href="/" title="Rick And Morty")
                img(:src="logo" alt="Rick And Morty")

</template>

<script>

export default {
    name: 'Header',
    data() {
        return {
            logo: require('@/assets/img/logo.png'),
        }
    }
}
</script>
