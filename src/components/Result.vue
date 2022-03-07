<template>
    <p>Reaction Time: {{ result }}ms</p>
    <p>{{ rank }}</p>
</template>

<script>
export default {
    props: ["result"],
    data() {
        return {
            rank: null,
        };
    },
    mounted() {
        if (this.result < 250) {
            this.rank = "Godspeed";
        } else if (this.result < 400) {
            this.rank = "Nice speed";
        } else {
            this.rank = "Snail pace...";
        }
    },
};
</script>

<style>
</style>