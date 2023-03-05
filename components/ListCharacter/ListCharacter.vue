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
</template>

<script>
import CardCharacter from './CardCharacter.vue'

    export default {
        name: 'ListCharacter',
        components: {
            CardCharacter
        },
        props: {
            characters: {
                type: Array,
                default() { return [] }
            }
        }
    }
</script>

