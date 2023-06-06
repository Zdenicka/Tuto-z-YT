<template>
    <div class="ninja">
        <h1>Ninja reaction timer</h1>
        <p></p>
        <q-btn class="glossy" rounded 
            color="cyan-8" 
            icon-right="send"
            @click="start" 
            :disable="isPlaying"
            label="Play" />
    </div>
    <Block v-if= "isPlaying" :delay = "delay" @end= "endGame" />
    
    <Result v-if= "showResults" :score= "score"  />
</template>

<script>
import Block from './Block.vue'
import Result from './Resu.vue'

export default {
    name: 'ninja',
    components: {Block, Result},
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
            showResults: false,
        }
    },
    methods:{
        start() {
            this.delay = 2000 + Math.random() * 5000
            this.isPlaying = true
            this.showResults = false
        },
        endGame(reactionTime) {
            this.score = reactionTime
            this.isPlaying = false
            this.showResults = true
        }

    }
}
</script>
