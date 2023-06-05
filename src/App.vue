<template>
  <compo-1/>
  <ninja/>
</template>

<script>
import compo1 from './components/compo1.vue'
import ninja from './components/ninja-timer.vue'


export default {  
  name: 'app',
  components: {
      compo1, ninja
  }
}
  </script>