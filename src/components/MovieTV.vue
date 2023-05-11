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

    },
    methods: {
        // bandiera
        flaf(e) {
            // this.propsMovie.original_language
            e = e.toUpperCase()
            if (e == 'EN') {
                e = 'BG'
                return `https://flagsapi.com/${e}/flat/64.png`;
            } else {
                return `https://flagsapi.com/${e}/flat/64.png`;
            }
        },
        // stelle
        star(x) {
            return Math.ceil(x / 2)
        }

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
            <p class="card-text">{{ star(propsMovie.vote_average) }}</p>
            <img :src="flaf(propsMovie.original_language)" style="width: 30px;">
            <!-- <span class="card-text">{{ propsMovie.original_language }}</span> -->
            <div>
                <i v-for="n in 5" class="fa-star empty"
                    :class="(n <= star(propsMovie.vote_average)) ? 'fa-solid text-warning' : 'fa-regular'"></i>
            </div>
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
        opacity: 0;

        .card-text {
            font-size: .8rem;
        }

        span {}

        &:hover {
            opacity: 1;
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