<template>
    <div class="playgroundBtn" @click="stopTimer" v-if="show">Click</div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            show: false,
            timer: null,
            reactionTimer: 0
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('showResult', this.reactionTimer)
            this.$emit('showResult', this.reactionTimer)
        }
    },
    mounted() {
        setTimeout(() => {
            this.show = !this.show
            this.startTimer();
        }, this.delay)
    },

};
</script>

<style>
.playgroundBtn {
    margin: 30px auto;
    width: 300px;
    border-radius: 10px;
    color: white;
    height: 200px;
    background: #0fc10f;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>