<script>
import SerieTVVue from './SerieTV.vue';
import MovieTV from './MovieTV.vue';
import FilmsPopular from './FilmsPopular.vue';
import { store } from '../store';
export default {
    name: 'MainComp',
    props: ['propsFilm'],
    components: {
        SerieTVVue,
        MovieTV,
        FilmsPopular,
    },
    data() {
        return {
            store
        }
    },
    created() {
    },
    methods: {
    }
}
</script>
<template>
    <div class="container">
        <main class="d-flex flex-wrap gap-1 m-1">


            <!-- movie -->

            <div class="d-flex flex-wrap gap-1 m-1">
                <MovieTV v-for="( item, index ) in  store.arrayMovies " :key="index" :propsMovie="item">
                </MovieTV>
            </div>
            <!-- serieTV -->
            <div class="d-flex flex-wrap gap-1 m-1">
                <SerieTVVue v-for="(item, index) in store.arraySerieTV" :key="index" :propsSeriesTV="item"></SerieTVVue>
            </div>

            <!-- films-popolari -->
            <div class=" d-flex flex-wrap gap-1 m-1">
                <FilmsPopular v-for="(item, index) in store.arrayFilm" :key="index" :propsFilmPopular="item"></FilmsPopular>
            </div>
        </main>
    </div>
</template>
<style lang="scss" scoped>
.container {
    .card {
        display: flex;

        img {
            .card-body {
                p {
                    display: none;
                }

                p:hover {
                    filter: brightness(80);
                    display: block;
                }
            }
        }
    }
}
</style>