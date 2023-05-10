<script>
import { store } from '../store';
export default {
    name: 'FilmsPopular',
    props: ['propsFilmPopular'],
    data() {
        return {
            store,
        }
    },
    created() {

    }

}
</script>
<template>
    <div class="card " style="max-width: 8rem;">
        <img :src="`https://image.tmdb.org/t/p/w342/` + propsFilmPopular.poster_path" class="card-img-top"
            :alt="propsFilmPopular.title">
        <div class="card-body">
            <p class="card-text mb-0">{{ propsFilmPopular.original_title }}</p>
            <img v-if="propsFilmPopular.original_language == 'en'" src="https://flagsapi.com/GB/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'fr'" src="https://flagsapi.com/FR/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'nl'" src="https://flagsapi.com/NL/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'en'" src="https://flagsapi.com/GB/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'it'" src="https://flagsapi.com/IT/flat/64.png"
                style="width: 30px;">
            <!-- <span>{{ propsFilmPopular.original_language }}</span> -->
        </div>
    </div>
</template>
<style lang="scss" scoped>
.card {
    position: relative;

    img {
        width: 100%;
    }

    .card-body {
        position: absolute;


        .card-text {}

        &:hover {
            visibility: visible;
            top: 0px;
            bottom: 0px;
            right: 0px;
            left: 0px;
            color: #ffffff;
            background-color: rgba(32, 31, 31, 0.949);
        }
    }

}
</style>