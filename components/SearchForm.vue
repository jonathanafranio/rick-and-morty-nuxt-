<template lang="pug">
    form.form-search
        label.form-search__label(for="search") Buscar personagem:

        div.form-search__wrap
            select.form-search__select(name="genero")
                option(value="") Status de vida
                option(value="alive") Vivo(a)
                option(value="dead") Morto(a)
                option(value="unknown") Desconhecido

        div.form-search__wrap
            select.form-search__select(name="genero")
                option(value="") Todos os Gêneros
                option(value="female") Feminino
                option(value="male") Masculino
                option(value="genderless") Sem Gênero
                option(value="unknown") Desconhecido


        div.form-search__wrap
            input.form-search__input(type="text" id="search" placeholder="Por nome" v-model="search_input")
            button.form-search__btn
                svg.form-search__svg(viewBox="0 0 22 22" fill="none" xmlns="http://www.w3.org/2000/svg")
                    path(d="M9.75007 18.5001C14.5826     18.5001 18.5001 14.5826 18.5001 9.75007C18.5001 4.91754 14.5826 1 9.75007 1C4.91754 1 1 4.91754 1 9.75007C1 14.5826 4.91754 18.5001 9.75007 18.5001Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round")
                path(d="M15.9374 15.9377L21 21.0002" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round")
</template>

<script>
export default {
    data(){
        return {
            search_input: ''
        }
    }
}
</script>
