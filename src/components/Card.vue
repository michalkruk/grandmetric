<template>
    <div class="card rounded-md bg-white shadow-md max-w-sm">
        <div class="h-16 rounded-t-md" :class="colors[getRandomNumber()]"></div>
        <img class="-mt-8 mx-auto mb-2" :src="joke.icon_url" alt="chuck" />
        <div class="flex flex-col items-between px-6 py-3">
            <h2 class="mb-4 font-medium">{{ joke.value }}</h2>
            <div class="mb-4">
                <span class="uppercase text-gray-400 font-medium text-sm"
                    >Categories</span
                >
                <p v-for="(category, index) in joke.categories" :key="index">
                    {{ category }}
                </p>
                <p v-if="joke.categories.length === 0">none</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["joke"],
    data() {
        return {
            colors: [
                "bg-red-300",
                "bg-pink-300",
                "bg-blue-300",
                "bg-green-300",
                "bg-yellow-300",
                "bg-indigo-300",
                "bg-purple-300",
            ],
        };
    },
    methods: {
        getRandomNumber() {
            return Math.floor(Math.random() * 6);
        },
    },
};
</script>

<style>
.card {
    min-width: 250px;
}
</style>
