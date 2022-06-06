<template>
    <div class="form">
        <div class="form__flex">
            <h1>Pridať zákazníka</h1>
            <button @click="emit('close-form')">X</button>
        </div>
        <form @submit="onSubmit" class="form__form" action="">
        <label for="logo">
            <p class="form__text">Logo</p>
            <input class="form__input" @change="onFileSelected"  type="file" accept="image/png, image/jpeg, image/jpg">

        </label>
        <label for="name">
            <p class="form__text">Name</p>
            <input class="form__input" placeholder="Enter Name" v-model="name" type="text">

        </label>
        <label for="com_id">
            <p class="form__text">COM ID</p>
            <input class="form__input" placeholder="Enter COM ID" v-model="com_id" type="text" name="" id="">

        </label>
        <label for="leg_id">
            <p class="form__text">LEG ID</p>
            <input class="form__input" type="text" placeholder="Enter LEG ID" v-model="leg_id">

        </label>
        <label for="size">
            <p class="form__text">SIZE</p>
            <input class="form__input" placeholder="hint: 123 GB" v-model="size" type="text" name="" id="">

        </label>
       
       <div class="form__add">
            <button class="form__add-button">Pridať zákazníka</button>
       </div>
        </form>
        
    </div>
</template>

<script>
//import { reactive, toRefs } from 'vue'
import axios from 'axios'
export default {
    props: ['customer'],
    data() {
        return {
            id: '',
            logo: null,
            name: '',
            com_id: '',
            leg_id: '',
            status: 'active',
            enabled: true,
            size: '',
            selectedFile: null,

        }
    },
    methods: {
        async addCustomer( customer) {
        await axios
        .post('http://localhost:3000/api/v1/customers', customer)
        .then((response) => {
          response.data
        })
        },
        onSubmit(e) {
            e.preventDefault()
            const customer = {
                logo: 'enterprise.jpg',
                name: this.name,
                com_id: this.com_id,
                leg_id: this.leg_id,
                status: 'active',
                enabled: true,
                size: this.size
            }
            this.addCustomer(customer)
            console.log(customer)
        },
        onFileSelected(event) {
            console.log(event.target.files[0])
            
        }
    },
    setup (props, { emit }) {
        return {
           emit
        }
    }
}
</script>

