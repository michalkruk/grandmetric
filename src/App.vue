<template>
    <div class="flex flex-col m-auto p-4">
        <h1 class="text-center text-4xl font-bold my-6">Chuck Norris jokes</h1>
        <InfiniteScroll />
    </div>
</template>

<script>
import InfiniteScroll from "./components/InfiniteScroll.vue";

export default {
    name: "App",
    components: {
        InfiniteScroll,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    height: 100%;
    min-height: 100vh;
    background-color: #e9e9e9;
}
</style>
