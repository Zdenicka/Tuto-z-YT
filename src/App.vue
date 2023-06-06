<template>
  <compo-1/>
  <ninja/>
  <formular/>
</template>

<script>
import compo1 from './components/uvod/compo1.vue'
import ninja from './components/ninja/ninja-timer.vue'
import formular from './components/formular/Formular.vue'


export default {  
  name: 'app',
  components: {
      compo1, ninja, formular
  }
}
  </script>