<template>
    <div>
        <div>
            <TheHeader2 v-if="showHeader"/>
            <h1>Hello World</h1>
            <br>
            <input v-model="name" type="text">
            {{name}}
            <br>
        </div>
<br><br>
        <button @click="showHeader = !showHeader" >
            Ativar e desativar header
        </button>


    </div>

</template>
<script>

import TheHeader2 from './components/TheHeader2.vue'

export default {
    name: "App",
    data() {
        return {
            name: "Kelvin R",
            showHeader: true,
        };
    },    
    beforeUpdate(){
        console.log('beforeUpdate', this.name)
    },
    updated(){
        console.log('updated', this.name)
    },
    // beforeCreate() {
    //     console.log("beforeCreate");
    //     console.log("Estado: " + this.name);
    //     console.log("DOM: ", this.$el);
    // },
    // created() {
    //     console.log("created");
    //     console.log("Estado: " + this.name);
    //     console.log("DOM: ", this.$el);
    // },
    // beforeMount() {
    //     console.log("beforeMount");
    //     console.log("Estado: " + this.name);
    //     console.log("DOM: ", this.$el);
    // },
    // mounted() {
    //     console.log("mounted");
    //     console.log("Estado: " + this.name);
    //     console.log("DOM: ", this.$el);
    // },

    watch: {},
    computed: {},
    methods: {},
    components: { TheHeader2 }
}

</script>
  
  
  
<style >

</style>
  