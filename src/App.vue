<template>
    <h1>Reaction Timer</h1>
    <button @click="startGame" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResult" :result="result" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
    name: "App",
    components: { Block, Result },
    data() {
        return {
            showResult: false,
            isPlaying: false,
            delay: null,
            result: null,
        };
    },
    methods: {
        startGame() {
            this.delay = 2000 + Math.random() * 5000;
            this.isPlaying = true;
            this.showResult = false;
        },
        endGame(reactionTime) {
            this.result = reactionTime;
            this.isPlaying = false;
            this.showResult = true;
        },
    },
};
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
button {
    padding: 0.5em 1.5em;
    color: white;
    background-color: teal;
    border: 0;
    border-radius: 10px;
    cursor: pointer;
}

button:hover {
    background-color: hsl(180, 100%, 35%);
}

button[disabled] {
    cursor: not-allowed;
    opacity: 0.5;
}
</style>
