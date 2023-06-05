<template>
  <div class="bedna" v-if="showBlock">
    Click me
  </div>
</template>

<script>

export default {
    props: [
        'delay'],
    data(){
        return {
            showBlock: false    
        }
    },
    mounted() {
        console.log('component mounted')
        setTimeout(() =>{
            this.showBlock = true
            console.log(this.delay)
        }, this.delay)
    },
    updated() {

    }


}
</script>

<style>

</style>