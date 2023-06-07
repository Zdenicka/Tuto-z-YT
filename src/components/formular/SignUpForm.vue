<template>
   <div class="form">
        <div class="m-a-xl" style="max-width: 500px">
            <q-form
            class="q-gutter-md"
            >
                <q-input
                    filled
                    type="email"
                    v-model= "email"
                    label="email *"
                    hint="email *"
                    lazy-rules
                    :rules="[ val => val && val.length > 0 || 'Please type something']"
                />

                <q-input
                    filled
                    type="password"
                    v-model= "password"
                    label="password *"
                    hint="password"
                    lazy-rules
                    :rules="[ val => val && val.length > 8 || 'Must be longer than 8 char']"
                />

                <q-select 
                    filled
                    hint="role"
                    v-model="role" 
                    :options="options" 
                    label="role" 
                    />

                <q-input
                    filled
                    type="number"
                    label="Your age *"
                    lazy-rules
                    :rules="[
                    val => val !== null && val !== '' || 'Please type your age',
                    val => val > 0 && val < 100 || 'Please type a real age'
                    ]"
                />


                <div>
                    <q-checkbox keep-color v-model="check" label="Accept terms and conditions" color="teal" />
                </div>

                <div class="q-gutter-sm">
                    <q-checkbox v-model="psi" val="Bohoušek" label="Bohoušek" color="teal" />
                    <q-checkbox v-model="psi" val="Charles" label="Charles" color="teal" />
                    <q-checkbox v-model="psi" val="Dorotka" label="Dorotka" color="teal" />
                </div>

                <q-input
                    filled
                    type="tricks"
                    v-model= "tempTricks"
                    label="tricks"
                    hint="tricks (oddělujte čárkou)"
                    @keyup="AddTrick"
                />

                <span 
                    v-for= "(trick, index) in tricks" 
                    :key="index"
                    class="q-gutter-xs">
                    
                    <q-btn color="teal-3" 
                    rounded no-caps
                    @click= "removeTrick(index)">
                        {{trick}}
                    </q-btn>
                </span>
                <div>
                    <q-btn class="glossy" rounded color="teal" label="Create account" />
                </div> 
            </q-form>
        </div>
            <p>email: {{ email }}</p>
            <p>password: {{ password }}</p>
            <p>role: {{ role }}</p>
            <p>psi:
                <ul>
                    <li v-for= "(pes, index) in psi" :key="index">{{pes}}</li> 
                </ul>
            </p>
            
        
    </div>
</template>

<script>
export default {
    data(){
        return {
            email: '',
            password: '',
            role: '',
            options: ['Web designer', 'Web developer'],
            check: false,
            psi: [],
            tempTricks: '',
            tricks: []
        }
    },
    methods: {
        AddTrick(e) {
            if (e.key === ',' && this.tempTricks.length > 1) {
                if (!this.tricks.includes(this.tempTricks.substring(0, this.tempTricks.length - 1))) {
                    this.tricks.push(this.tempTricks.substring(0, this.tempTricks.length - 1))
                }
                this.tempTricks = ''
            }
        },
        removeTrick(index){
            this.tricks.splice(this.tricks.indexOf(index), 1);
        }

    }


}
</script>

<style>

</style>