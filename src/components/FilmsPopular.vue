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
            return Math.ceil(this.propsFilmPopular.vote_average / 2)
        }
    }

}
</script>
<template>
    <div class="card " style="max-width: 8rem;">
        <img :src="`${store.pathImg}${propsFilmPopular.poster_path}`" class="card-img-top" :alt="propsFilmPopular.title">
        <div class="card-body p-1">
            <p class="card-text mb-0">{{ propsFilmPopular.original_title }}</p>
            <p class="card-text mb-0">{{ propsFilmPopular.overview }}</p>
            <p class="card-text mb-0">{{ star() }}</p>
            <img :src="flag(propsFilmPopular.original_language)" style="width: 20px;">
            <!-- <img v-else-if="propsFilmPopular.original_language == 'fr'" src="https://flagsapi.com/FR/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'nl'" src="https://flagsapi.com/NL/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'es'" src="https://flagsapi.com/ES/flat/64.png"
                style="width: 30px;">
            <img v-else-if="propsFilmPopular.original_language == 'it'" src="https://flagsapi.com/IT/flat/64.png"
                style="width: 30px;"> -->
            <!-- <span>{{ propsFilmPopular.original_language }}</span> -->
            <div>
                <i v-for="n in 5" class="fa-star empty" :class="(n <= star()) ? 'fa-solid text-warning' : 'fa-regular'"></i>
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
        z-index: 1;
        position: absolute;
        // visibility: hidden;
        opacity: 0;

        .card-text {
            font-size: .4rem;
        }

        &:hover {
            // visibility: visible;
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