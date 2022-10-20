<template>
    <div>
        <header>
            <h1><slot name="title"/></h1>
            <slot/>
        <slot name="description"/>
        </header>

        <h1>TheHeader2</h1>

    </div>

</template>

<script>
import { computed } from '@vue/reactivity'

export default {
    mounted(){
        console.log(this.$el)
        console.log(this.$slots)
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