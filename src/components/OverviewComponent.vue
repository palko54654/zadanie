<template>
<div class="overview">
    <div class="overview__content">
        <h1 class="overview__heading">Customer Overview</h1>
        <div class="overview__flex">
            
            <input v-model="searchWordd" class="overview__searchbar" type="text" placeholder="Customer or ID" >
            <button @click="emit('show-form')" class="overview__addbutton"><i class="overview__plus fa-solid fa-plus"></i></button>
        </div>
    </div>
    <div class="table">
        <div class="table__header">
            <p class="table__header-name">Customer</p>
            <p class="table__header-name"></p>
            <p class="table__header-name">COM ID</p>
            <p class="table__header-name">LEG ID</p>
            <p class="table__header-name">SIZE</p>
            <p class="table__header-name">STATUS</p>
        </div>
        <div class="table__container">
        <TableComponent v-for="customer in filteredCustomers" :key="customer.id" :customer="customer"/>
        </div>
    </div>
</div>
</template>

<script>
//import { reactive, toRefs } from 'vue'
import TableComponent from '@/components/TableComponent.vue'
import axios from 'axios'

export default {
    components: {
    TableComponent,
    },
    data() {
        return {
            customers: [],
            searchWord: null,
            filteredCustomers: null,
        }
    },
    methods: {
        async getCustomers() {
            try {
                const response = await axios.get("http://localhost:3000/api/v1/customers");
                this.customers = response.data
                this.filteredCustomers = this.customers
            } catch (error) {
                console.log(error);
            }
        },


        filteredCustomer(word) {
              if (!word || word === '{}') {
                this.searchWord = null
                this.filteredCustomers = this.customers
            
              } else {
                this.searchWord = word

                word = word.trim().toLowerCase()
                this.filteredCustomers = this.customers.filter((customer) => {
                return customer.name.toLowerCase().includes(word)
                })
              }
        }
        
    },
    created() {
        this.getCustomers();
        this.filteredCustomer();
    },  
    computed: {
      

        filterCustomers(){
            try {
                let a =
                this.filteredCustomers ||
                this.customers 

                return a
            } catch (e) {
                console.log(e)
            }
            return this.filteredCustomers
        },

        searchWordd: {
            get() {
             return   this.searchWord
            },
            set(value) {
                this.filteredCustomer(value)
            },
        },
    },
    setup (props, {emit}) {
        return { emit }
    }
}
</script>

