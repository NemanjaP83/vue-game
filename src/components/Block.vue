<template>
    <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>

export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('endGame', this.reactionTime)
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    }
}
</script>

<style scoped>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: teal;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>