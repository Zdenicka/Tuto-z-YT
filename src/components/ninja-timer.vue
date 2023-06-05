<template>
    <div class="ninja">
        <h1>Ninja reaction timer</h1>
        <p></p>
        <q-btn outline rounded 
            color="cyan-8" 
            icon-right="send"
            @click="start" 
            :disable="isPlaying"
            label="Play" />
    </div>
    <Block v-if= "isPlaying" :delay = "delay" />
</template>

<script>
import Block from './Block.vue'
export default {
    name: 'ninja',
    components: {Block},
    data() {
        return {
            isPlaying: false,
            delay: null
        }
    },
    methods:{
        start() {
            this.delay = 2000 + Math.random() * 5000
            this.isPlaying = true
        }

    }
}
</script>
