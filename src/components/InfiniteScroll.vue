<template>
    <div
        v-if="itemsToShow.length > 0"
        class="
            grid grid-cols-1
            md:grid-cols-2
            lg:grid-cols-3
            gap-4
            max-w-4xl
            m-auto
        "
    >
        <Card v-for="item in itemsToShow" :key="item.id" :joke="item" />
    </div>
    <div class="flex flex-col mt-4" v-else>
        <div class="flex m-auto mb-1">
            <div
                class="
                    bg-blue-300
                    p-2
                    w-4
                    h-4
                    m-1
                    rounded-full
                    animate-bounce
                    blue-circle
                "
            ></div>
            <div
                class="
                    bg-green-300
                    p-2
                    w-4
                    h-4
                    m-1
                    rounded-full
                    animate-bounce
                    green-circle
                "
            ></div>
            <div
                class="
                    bg-red-300
                    p-2
                    w-4
                    h-4
                    m-1
                    rounded-full
                    animate-bounce
                    red-circle
                "
            ></div>
        </div>
        <h3 class="m-auto font-bold text-gray-600">Loading</h3>
    </div>
    <Observer @intersect="intersected" />
</template>

<script>
import Observer from "./Observer";
import Card from "./Card.vue";
import axios from "axios";

export default {
    data: () => ({ page: 1, items: [], itemsToShow: [] }),
    mounted() {
        this.fetch();
    },
    methods: {
        async intersected() {
            this.page++;
            let items = this.items.slice(
                this.itemsToShow.length,
                this.itemsToShow.length + 10
            );
            this.itemsToShow = [...this.itemsToShow, ...items];
        },
        async fetch() {
            let jokes = await axios.get(
                "https://api.chucknorris.io/jokes/search?query=chuck"
            );

            this.itemsToShow = jokes.data.result.slice(0, 10);
            this.items = jokes.data.result;
        },
    },
    components: {
        Observer,
        Card,
    },
};
</script>

<style>
.blue-circle {
    animation-delay: 0.1s;
}
.green-circle {
    animation-delay: 0.2s;
}
.red-circle {
    animation-delay: 0.3s;
}
</style>
