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

    }

}
</script>
<template>
    <div class="card" style="max-width: 8rem;">
        <img v-if="propsSeriesTV.poster_path == null" :src="`https://picsum.photos/id/237/200/300`" alt="">
        <img :src="`https://image.tmdb.org/t/p/w342/` + propsSeriesTV.poster_path" class="card-img-top"
            :alt="propsSeriesTV.original_name">
        <div class="card-body">
            <p class="card-text">{{ propsSeriesTV.name }}</p>
            <p class="card-text">{{ propsSeriesTV.vote_average }}</p>
            <img v-if="propsSeriesTV.original_language == 'en'" src="https://flagsapi.com/GB/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsSeriesTV.original_language == 'fr'" src="https://flagsapi.com/FR/flat/64.png"
                style="width: 30px;">
            <!-- <span>{{ propsSeriesTV.original_language }}</span> -->

        </div>
    </div>
</template>
<style lang="scss" scoped>
.card {
    position: relative;

    img {
        width: 100%;
        height: 100%;


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