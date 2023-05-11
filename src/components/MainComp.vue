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
            <div v-if="this.store.arrayMovies.length">
                <h2 class="title"><em>Movie</em></h2>
                <div class="d-flex flex-wrap gap-1 m-1">
                    <MovieTV v-for="( item, index ) in  store.arrayMovies " :key="index" :propsMovie="item">
                    </MovieTV>
                </div>
            </div>
            <!-- serieTV -->
            <div v-if="this.store.arraySerieTV.length">
                <h2 class="title"><em>Serie</em></h2>
                <div class="d-flex flex-wrap gap-1 m-1">
                    <SerieTVVue v-for="(item, index) in store.arraySerieTV" :key="index" :propsSeriesTV="item"></SerieTVVue>
                </div>
            </div>

            <!-- films-popolari -->
            <div>
                <h2 class="title"><em>Popolari</em></h2>
                <div class="d-flex flex-wrap gap-1 m-1">
                    <FilmsPopular v-for="(item, index) in store.arrayFilm" :key="index" :propsFilmPopular="item">
                    </FilmsPopular>
                </div>
            </div>
        </main>
    </div>
</template>
<style lang="scss" scoped>
.title {
    color: rgb(192, 19, 19);
}
</style>