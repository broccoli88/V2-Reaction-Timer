<template>
    <div class="block" v-if="showBlock" @click="timerStop">Click ME</div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            reactionTime: null,
            timer: 0,
            showBlock: false,
        };
    },

    mounted() {
        setTimeout(() => {
            this.timerStart();
            this.showBlock = true;
        }, this.delay);
    },
    methods: {
        timerStart() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },

        timerStop() {
            clearInterval(this.timer);
            this.$emit("end", this.reactionTime);
        },
    },
};
</script>

<style>
.block {
    width: min(400px, 40vw);
    height: min(300px, 20vh);
    background-color: hsl(180, 100%, 30%);
    border: 2px solid hsl(180, 100%, 15%);
    margin: 3rem auto;
    border-radius: 10px;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>