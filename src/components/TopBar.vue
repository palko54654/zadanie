<template>
    <div class="topbar__content">
        <h3 class="topbar__heading">Site Amin</h3>
    </div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
    setup () {
        const state = reactive({
            count: 0,
        })
    
        return {
            ...toRefs(state),
        }
    }
}
</script>

