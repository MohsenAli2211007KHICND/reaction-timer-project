<template>
  <div class="block" v-if="showBlock" @click.self="stopTimer">
    Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data () {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted () {
        setTimeout(() => {
            this.showBlock = true
            this.startTime()
        }, this.delay);
    },
    methods: {
        startTime () {
        this.timer = setInterval(() =>{this.reactionTime += 10}, 10)            
        },
        stopTimer () {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
    // updated () {
    //     console.log("Block Component Updated!");
    // },
    // unmounted () {
    //     console.log("Block Component Unmounted!");
    // }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>