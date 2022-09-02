<template>
    <div class="container">
        <a href="https://rp76.ir">
            <h1>Hd Wallpaper.</h1>
        </a>
        <p class="text-muted">Hover the images for
            <select v-model="scale">
                <option v-for="item in [1.5,2,2.5,3,3.5]" :key="item">{{ item }}</option>
            </select>
            zoom, Click them for download.
        </p>
        <hr>
        <div class="row mx-auto justify-content-center">
            <a v-for="item in images" class="col-md-4 my-1 p-1 rp-hover" :href="item" :key="item" download="">
                <img class="img-fluid" :src="item" :alt="item">
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'App',
    data() {
        return {
            images: [],
            scale: 1.5
        }
    },
    mounted() {
        let requireModule = require.context("./assets/images", false, /\.*?/);

        this.images = requireModule.keys().map((item) => require("./assets/images" + item.replace(".", "")));
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

.rp-hover:hover {
    box-shadow: 3px 0 15px #999;
    transform: scale(v-bind("scale"));
    z-index: 10;
}
</style>
