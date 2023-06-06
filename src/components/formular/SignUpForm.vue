<template>
   <div class="form">
        <div class="q-pa-md" style="max-width: 500px">
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
                    <q-checkbox v-model="check" label="Accept terms and conditions" color="teal" />
                </div>
            </q-form>
            <div class="q-pa-md">
                <div class="q-gutter-sm">
                <q-checkbox v-model="psi" val="Bohoušek" label="Bohoušek" color="teal4" />
                <q-checkbox v-model="psi" val="Charles" label="Charles" color="teal4" />
                <q-checkbox v-model="psi" val="Dorotka" label="Dorotka" color="teal4" />
                </div>
            </div>

            
            <p>email: {{ email }}</p>
            <p>password: {{ password }}</p>
            <p>role: {{ role }}</p>
            <p>psi: {{psi}}</p> 
        </div>
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
            selection: []
        }
    }
    

}
</script>

<style>

</style>