<template>
    <h3>Reaction time: {{ reactionTime }} ms</h3>
    <p class="rank">{{ score }}</p>
    <h4>Play again!</h4>
</template>

<script>
export default {
    props: ['reactionTime'],
    data() {
        return {
            score: null
        }
    },
    mounted() {
    if (this.reactionTime < 300) {
        this.score = 'Exelent, fast fingers!'
    } else if (this.reactionTime < 400) {
        this.score = 'Good job!'
    } else {
        this.score = 'Try to be faster!'
        }
    }
}

</script>

<style scoped>
    .rank {
        color: crimson;
        font-size: 28px;
        font-weight: bold;
    }
</style>