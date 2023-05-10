<script >
import axios from 'axios';
import { store } from './store';
import SearchComp from './components/SearchComp.vue';
import MainComp from './components/MainComp.vue';

export default {
  name: 'AppVue',
  components: {
    SearchComp,
    MainComp,
  },
  data() {
    return {
      store,
    }
  },
  created() {
    this.api()
    // this.apiMovie()
    // this.apiFilms()
    // this.apiSerieTV()

  },
  methods: {
    api() {
      if (this.store.search != '') {
        this.apiMovie()
        this.apiSerieTV()
      } else {
        this.apiFilms()
      }

    },
    // api() {
    //   this.apiFilms()
    //   this.apiMovie()
    //   this.apiSerieTV()
    // },
    apiFilms() {
      axios.get(`https://api.themoviedb.org/3/movie/popular?api_key=${this.store.apiKey}`)
        .then((res) => {
          this.store.arrayFilm = res.data.results
          // console.log(this.store.arrayFilm)
        })
    },
    apiMovie() {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${store.apiKey}&query=${store.search}`)
        .then((res) => {
          this.store.arrayMovies = res.data.results
          console.log(res.data.results)
          // console.log(this.store.arrayMovies)
        })
    },
    apiSerieTV() {
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${store.apiKey}&query=${store.search}`)
        .then((res) => {
          console.log(res.data.results)
          this.store.arraySerieTV = res.data.results
        })
    }

  }



}

</script>

<template>
  <div class="wrapper">
    <SearchComp @searchFilm="api()"></SearchComp>
    <!-- ------main -->
    <MainComp></MainComp>
  </div>
</template>

<style lang="scss">
@use '../src/style/main.scss';
</style>
