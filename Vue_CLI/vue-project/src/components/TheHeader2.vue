<template>
    <div>

        <h1>TheHeader2</h1>

    </div>
    <section></section>

</template>

<script>
import { computed } from '@vue/reactivity'

export default {
    mounted(){
        window.addEventListener('resize', this.resize)
    },
    beforeUnmount() {
        console.log("beforeUnmount");
        window.removeEventListener('resize', this.resize)
    },
    unmounted() {
        console.log("unmounted");
    },
    methods:{
        resize($evt){
            console.log($evt)
        }
    },


    computed: {

    },

}

</script>

<style>

</style>