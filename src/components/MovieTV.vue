<script>
import { store } from '../store';
export default {
    name: 'MovieTV',
    props: ['propsMovie'],
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
    <div class="card" style="width: 8rem;">
        <img v-if="propsMovie.poster_path == null" src="https://picsum.photos/seed/picsum/200/300" alt="">
        <img v-else :src="'https://image.tmdb.org/t/p/w342/' + propsMovie.poster_path" class="card - img - top"
            :alt="propsMovie.title">
        <div class="card-body">
            <p class="card-text">{{ propsMovie.original_title }}</p>
            <p class="card-text">{{ propsMovie.vote_average }}</p>
            <img v-if="propsMovie.original_language == 'en'" src="https://flagsapi.com/GB/flat/64.png" style="width: 30px;">
            <img v-else-if="propsMovie.original_language == 'fr'" src="https://flagsapi.com/FR/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsMovie.original_language == 'nl'" src="https://flagsapi.com/NL/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsMovie.original_language == 'en'" src="https://flagsapi.com/GB/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsMovie.original_language == 'it'" src="https://flagsapi.com/IT/flat/64.png"
                style="width: 30px;">
            <span class="card-text">{{ propsMovie.original_language }}</span>

        </div>
    </div>
</template>
<style lang="scss" scoped>
.card {
    max-height: 100%;
    position: relative;

    img {
        width: 100%;
        min-height: 200px;
    }

    .card-body {
        position: absolute;


        .card-text {}

        span {}

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