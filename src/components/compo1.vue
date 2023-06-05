<template>
<h1>{{title}}</h1>
<p>Vítejte</p>
<input type="text" ref="name">
<q-btn outline rounded color="teal-10" @click= "handleClick" label="Click me" />
<q-btn outline rounded color="teal-10" @click= "toggleModal" label="Show modal"/>
<q-btn outline rounded color="teal-10" @click= "toggleModalTwo" label="Show second modal"/>

<!--další možnost, jak to udělat - tenhle modul jsem teleportovala do indexu a bude se zobrazovat odtamtud
je tam jako class a proto je tady s tečkou, můžu ho taky poslat jako id, pak tady nebude mít tečku, ale #.
Protože to dál není v app, nedědí to její stylopis, chce to na to myslet-->
<teleport to=".modal" v-if= "showModal">
  <Modal theme = "sale" @close="toggleModal">
            <!--tohle jde do slotu - funguje mi, jen pokud je před tím pojmenovaným -->
            <h1>Nadpis propsaný přes slot</h1>  
            <p>I tohle předávám potomkovi přes slot, oproti návodu to nejde předat přes nespecifikovaný slot, pokud to umístím za pojmenovaný slot.
             Stylopis řeším přes props</p> 
            <!--pojmenovaný slot pak můžu umisťovat v rámci modulu-->
            <template v-slot:links>
              <a href="#">Sign up</a>
              <a href="#">more info</a>
            </template>
  </Modal> 
</teleport>
<div v-if= "showModalTwo">
  <Modal theme = "dark" @close="toggleModalTwo">
            <!--tohle jde do slotu - funguje mi, jen pokud je před tím pojmenovaným -->
            <h1>Zkoušíme druhé modální okno</h1>  
            <p>A budu věřit, že bude fungovat</p> 
            <!--pojmenovaný slot pak můžu umisťovat v rámci modulu-->
            <template v-slot:links>
              <a href="#">Sign out</a>
              <a href="#">you dont want to know</a>
            </template>
  </Modal> 
</div>

</template>

<script>
import Modal from './Modal.vue'

export default {  
  name: 'compo1',
  components: {
      Modal
  },
  
  data() {
    return{
      title: 'Učíme se vue',
      showModal: false,
      showModalTwo: false,

    }
  },

  methods: {
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
    },
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo 
    }


  }

}
</script>

<style>

</style>
