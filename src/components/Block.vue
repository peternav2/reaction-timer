<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
        <p v-if="clicked"> {{ reactionTime }}</p>
    </div>

</template>



<script>
export default {
    props: ['delay'],
    // setTimeout(() => {}, delay) is a built-in JavaScript function that takes a function and a delay in milliseconds as arguments. It will execute the function after the delay has passed
    mounted() {
        console.log('mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            clicked: false
        }
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime+=10
            }, 10)
        },
        stopTimer() {
            console.log('clicked block')
            clearInterval(this.timer)
            this.clicked = true;
        }
    },
    updated() {
        console.log('updated')
    },
    unmounted() {
        console.log('unmounted')
    }
}

</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>

