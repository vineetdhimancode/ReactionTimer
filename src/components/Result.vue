<template>
    <p>Response time is : {{reactionTime}} ms</p>
    <div class="playgroundBtn" data="{{reactionTime}}" >{{resultText}}</div>
</template>

<script>
export default {
    name: 'Result',
    props: ['reactionTime'],
    data() {
        return {
            reaction: this.reactionTime,
            resultText: null
        }
    },
    methods: {
        getResultText() {
            if (this.reaction <= 400) {
                this.resultText = 'Super fast :)';
            } else if (this.reaction > 400 && this.reaction < 600) {
                this.resultText = 'Fast :)';
            } else if (this.reaction > 600) {
                this.resultText = 'Slow :('
            }
        }
    },
    mounted() {
        this.getResultText();
    }
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