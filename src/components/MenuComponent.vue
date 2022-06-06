<template>
    <div class="menu__content">
        <button class="menu__button" @click="menuShow = !menuShow">Show menu</button>
        <div class="menu__mobile" :class="{ show: menuShow}">
        <h4 class="menu__heading"> SITE ADMIN</h4>
        <h3 class="menu__item active"><i class="menu__icon activeicon fa-solid fa-earth-americas"></i> Customer Overview</h3>
        <h3 class="menu__item"><i class="menu__icon-a fa-solid fa-ellipsis-vertical" style="margin-right:1px"></i><i class="menu__icon fa-solid fa-bars"></i> Reports</h3>
        <h3 class="menu__item"><i class="menu__icon fa-solid fa-file-circle-plus"></i>File transcodings</h3>
        <h3 class="menu__item"><i class="menu__icon fa-solid fa-bell"></i> Notification Center</h3>
        </div>
    </div>
</template>

<script>
//import { reactive, toRefs } from 'vue'

export default {
    data() {
        return {
            menuShow: false
        }
    },
    methods: {
       
    },
    setup () {
       
    }
}
</script>

