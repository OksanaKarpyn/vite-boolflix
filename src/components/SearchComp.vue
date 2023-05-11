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
            <button type="submit" @click="$emit('searchFilm')"><i class="fa-solid fa-magnifying-glass"
                    style="color: #e60505;"></i></button>
        </div>
    </header>
    <div>

    </div>
</template>
<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid rgb(245, 10, 10);

    .title {
        flex-grow: 1;

        h1 {
            display: inline-block;
            color: rgb(255, 0, 0);
            box-shadow: 5px 5px 5px rgb(78, 6, 6);
            border-radius: 10px;

        }
    }

    .searchInput {
        input {
            padding: 5px;
            background-color: rgba(84, 13, 13, 0.644);
        }

        button {
            padding: 6px 10px;
            border-radius: 5px;
            background-color: rgba(84, 13, 13, 0.644);
        }
    }
}
</style>