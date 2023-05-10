<script>
import { store } from '../store';
export default {
    name: 'SearchComp',
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
    <header class="container">
        <div class="title">
            <h1>BoolFlix</h1>
        </div>
        <div class="searchInput ">
            <input type="text" placeholder="search movies" v-model="store.search">
            <button type="submit" @click="$emit('searchFilm')">Search</button>
        </div>
    </header>
</template>
<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid red;

    .title {
        flex-grow: 1;

        h1 {
            color: red
        }
    }

    .searchInput {
        input {
            padding: 5px;
        }

        button {
            padding: 6px 10px;
            border-radius: 5px;
        }
    }
}
</style>