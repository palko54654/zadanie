<template>
    
        <div class="table__content">
            <div class="table__content-flex">
                <div class="table__content-logo" :style="{ 'background': 'url(' + require('../assets/customers/' + customer.logo) + ') no-repeat center'  }">a</div>
                <p class="table__content-text">{{ customer.name }}</p>
            </div>
            <div class="table__content-dropdown">
                <button @click="toggleMenu" class="table__content-button">Default</button>
                <div v-if="showDropdown" class="table__content-dropdown-menu">
                    <div class="table__content-dropdown-item">
                    <button @click="toggleSubMenu">Something</button>
                    </div>
                    <div class="table__content-dropdown-item">
                    <button @click="toggleSubMenu">Something</button>
                    </div>
                    <div class="table__content-dropdown-item">
                    <button @click="toggleSubMenu">Something</button>
                    </div>
                    <div class="table__content-dropdown-submenu" v-if="showSubdropdown">
                        <div class="table__content-dropdown-item">
                            <button>Something</button>
                        </div>
                        <div class="table__content-dropdown-item">
                            <button>Something</button>
                        </div>
                        <div class="table__content-dropdown-item">
                            <button>Something</button>
                        </div>
                    </div>
                </div>
            </div>
           <p class="table__content-text">{{ customer.com_id }}</p>
           <p class="table__content-text">{{ customer.leg_id }}</p>
           <p class="table__content-text">{{ customer.size }}</p>
           <p class="table__content-status">{{ customer.status }}</p>
           
        </div>
        
    
</template>

<script>
import { toRefs, reactive } from 'vue'
export default {
    props: ['customer'],
    methods: {



    },
    setup () {
        const state = reactive({
            showDropdown: false,
            hideDropdown: false,
            showSubdropdown: false,
            hideSubdropdown: false,
        })
        const toggleMenu = () => {
            if (state.showDropdown == state.hideDropdown) {
                state.showDropdown = true
            } else {
                state.showDropdown = false
            }
        }
        const toggleSubMenu = () => {
            if (state.showSubdropdown == state.hideSubdropdown) {
                state.showSubdropdown = true
            } else {
                state.showSubdropdown = false
            }
        }

        return {
            ...toRefs(state),
            toggleMenu,
            toggleSubMenu
        }
    }
}
</script>

