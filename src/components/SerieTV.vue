<script>
import { store } from '../store';
export default {
    name: 'SerieTV',
    props: ['propsSeriesTV'],
    data() {
        return {
            store,
        }
    },
    created() {
    },
    methods: {
        // bandiere
        flag(e) {
            e = e.toUpperCase()
            if (e == 'EN') {
                e = 'GB'
                return `https://flagsapi.com/${e}/flat/64.png`
            } else {
                return `https://flagsapi.com/${e}/flat/64.png`
            }
        },
        // stelle
        star() {
            // contero numero intero divido in 2
            return Math.ceil(this.propsSeriesTV.vote_average / 2)
        }
    }

}
</script>
<template>
    <div class="card" style="max-width: 8rem;">
        <img v-if="propsSeriesTV.poster_path == null" :src="`https://picsum.photos/id/237/200/300`" alt="">
        <img :src="`https://image.tmdb.org/t/p/w342/` + propsSeriesTV.poster_path" class="card-img-top"
            :alt="propsSeriesTV.original_name">
        <div class="card-body">
            <p class="card-text mb-0">{{ propsSeriesTV.name }}</p>
            <p class="card-text mb-0">{{ star() }}</p>
            <img :src="flag(propsSeriesTV.original_language)" style="width: 30px;">
            <!-- <span>{{ propsSeriesTV.original_language }}</span> -->
            <div>
                <!-- v-for * 5  :class dinamico condizione -->
                <i v-for="n in 5" class="fa-star" :class="(n <= star()) ? 'fa-solid text-warning' : 'fa-regular'"></i>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
.card {
    position: relative;

    .card-body {
        position: absolute;
        opacity: 0;

        .card-text {
            font-size: .4rem;
        }

        &:hover {
            opacity: 1;
            top: 0px;
            bottom: 0px;
            right: 0px;
            left: 0px;
            color: #ffffff;
            background-color: rgba(32, 31, 31, 0.949);
        }

        i {
            font-size: 10px;
        }
    }

}
</style>