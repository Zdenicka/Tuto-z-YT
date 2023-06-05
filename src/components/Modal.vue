<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme === 'sale'}">
            <!--default content se objeví, pokud nezadám žádný obsah do nepojmenovaného slotu -->
            <slot>default content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['theme'],
    methods: {
        closeModal(){
            this.$emit('close')
        }
    }
}

</script>




<!--scoped znamená, že tyhle styly budou fungovat jen v rámci tohodle komponentu, jinak jsou schopny přerazit i styl stejného názvu v nadřazené komponentě - při větším využití může být náročné na načítání stránky
- scoped nemůžu využít u hlavní/první vue stránky projektu
druhá varianta je, že tady víc specifikuju při názvu stylu a zaznamenám ho třeba jako ".modal h1" - tím určím, že se vztahuje jen na h1 v komponentě modal
stylem zadaným v  rámci komponenty přejedu styl z externího css souboru-->
