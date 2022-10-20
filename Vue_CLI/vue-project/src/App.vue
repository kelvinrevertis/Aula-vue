<template>

    <div>
        <p class="card">Teste CSS</p>
        <BaseCard/>
        <br>
    </div>

    <div>
        <div>
            <TheHeader2 v-if="showHeader">
            <h1>Home</h1>
            <p>Paragrafo de Teste</p>

                <template v-slot:description>
                    <p>Area do paragrafo de teste descrição</p>
                </template>

                <template v-slot:title>
                Slot Título    
                </template>

            </TheHeader2>


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
import BaseCard from '@/components/BaseCard.vue';

export default {
    name: "App",
    data() {
        return {
            name: "Kelvin R",
            showHeader: true,
        };
    },    
    // beforeUpdate(){
    //     console.log('beforeUpdate', this.name)
    // },
    // updated(){
    //     console.log('updated', this.name)
    // },
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
    components: { TheHeader2, BaseCard }
}

</script>
  
  
  
<style >

</style>
  