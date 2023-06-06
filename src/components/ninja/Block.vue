<template>
  <div class="bedna" v-if="showBlock" @click="stopTimer">
    Click me
  </div>
</template>

<script>

export default {
    props: [
        'delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,    
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() =>{
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay)
    },
    updated() {
        console.log('component updated')     
    },
    unmounted() {
        console.log('component unmounted')
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end', this.reactionTime)
        }
    }


}
</script>

<style>

</style>