<template lang="pug">
    nav.pagination
        a.pagination__first(
            :href="first_page"
            v-if="active > 1"
        ) Primeira
        span.pagination__first.-disable(v-else) Primeira

        a.pagination__prev(
            :href="prev_page"
            v-if="active > 1"
        ) Anterior
        span.pagination__prev.-disable(v-else) Anterior

        ul.pagination__ul
            li.pagination__li(
                v-for="p in pages_num"
                v-bind:key="p"
            )
                a.pagination__link(
                    :href="p.link"
                    :class="p.number == active ? '-active' : ''"
                ) {{ p.number }}


        a.pagination__next(
            :href="next_page"
            v-if="active < last"
        ) Próxima
        span.pagination__next.-disable(v-else) Próxima

        a.pagination__last(
            :href="last_page"
            v-if="active < last"
        ) Última
        span.pagination__last.-disable(v-else) Última
</template>

<script>
    export default {
        name: 'Pagination',
        props: {
            next: Number,
            prev: Number,
            active: Number,
            last: Number,
            prefix_url: String,
            search: {
                type: String,
                default() { return '' }
            },
        },
        computed: {
            prev_page(){
                const url = this.prev < 2 ? this.prefix_url : `${this.prefix_url}/p/${this.prev}`;
                return `${url}/${this.search}`
            },
            next_page(){
                const url = this.next < this.last ? `${this.prefix_url}/p/${this.next}` : `${this.prefix_url}/p/${this.last}`
                return `${url}/${this.search}`
            },
            first_page(){
                const url = `${this.prefix_url}`
                return `${url}/${this.search}`
            },
            last_page(){
                const url = `${this.prefix_url}/p/${this.last}`
                return `${url}/${this.search}`
            },
            pages_num(){
                const array_pages = [];
                if(this.prev) {
                    const obj_prev = {
                        number: this.prev,
                        link: this.prev_page
                    }
                    array_pages.push(obj_prev);
                }
                const active_page = {
                    number: this.active,
                    link: ''
                };
                array_pages.push(active_page)

                if(this.next) {
                    const obj_next = {
                        number: this.next,
                        link: this.next_page
                    };
                    array_pages.push(obj_next);
                }

                if(this.active == 1 && this.last > 2) {
                    const third = {
                        number: 3,
                        link: `${this.prefix_url}/p/3/${this.search}`
                    };
                    array_pages.push(third);
                }

                return array_pages;

            },

        }
    }
</script>

<style lang="scss" scoped>

</style>
