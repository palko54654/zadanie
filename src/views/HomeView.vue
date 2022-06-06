<template>
<main>
  <div id="overlay" class="overlay" v-if="overlay" key="-1">

  </div>
  <div class="container">
    
    <div class="topbar">
      <TopBar/>
    </div>
    <div class="grid">
    <div class="menu">
      <MenuComponent/>
    </div>
    <div class="content">
      <OverviewComponent @show-form="showForm" />
    </div>
    </div>
  </div>
    <transition name="addform">
    <AddCustomer v-if="isShowed" @close-form="hideForm" />
    </transition>
</main>  
</template>

<script>
// @ is an alias to /src
import { reactive, toRefs } from 'vue'
import TopBar from '@/components/TopBar.vue'
import MenuComponent from '@/components/MenuComponent.vue'
import OverviewComponent from '@/components/OverviewComponent.vue'
import AddCustomer from '@/components/AddCustomer.vue'

export default {
  name: 'HomeView',
  components: {
    TopBar,
    MenuComponent,
    OverviewComponent,
    AddCustomer
},
setup () {
  const state = reactive({
            isShowed: false,
            overlay: false,
        })
        const showForm = () => {
            state.isShowed = true
            state.overlay = true
        }
         const hideForm = () => {
          state.isShowed = false
          state.overlay = false
        }
        return{
            ...toRefs(state),
            showForm,
            hideForm,
        }
}
}
</script>

<style scoped>
    .addform-enter-active,
.addform-leave-active {
  transition: all 0.5s;
}
.addform-enter-from,
.addform-leave-to {
  opacity: 0;
  transform: translateY(-25%);
}



</style>
