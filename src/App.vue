<template>
  <compo-1/>
  <ninja/>
  <form/>
</template>

<script>
import compo1 from './components/uvod/compo1.vue'
import ninja from './components/ninja/ninja-timer.vue'
import form from './components/formular/Form.vue'


export default {  
  name: 'app',
  components: {
      compo1, ninja, form
  }
}
  </script>