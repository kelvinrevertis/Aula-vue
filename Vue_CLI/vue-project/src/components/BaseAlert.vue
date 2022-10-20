<template>
    <!-- <div :class="['alert', {'alert-success': variant==='success',
    'alert-danger': variant==='danger'}]">
        Seu formulario foi enviado com sucesso!
    </div> -->
    <br><br>
    <div :class="baseClass">
        {{ test }}
        <slot />
        <button @click="onClick">X</button>
    </div>
</template>

<script>
export default {
    emits: ["close"],
    props: {
        variant: {
            type: String,
            default: ''
        },
        test: {
            type: String,
            default: 'test'
        },
    },
    computed: {
        baseClass() {
            return [
                'alert',
                this.variant ? `alert-${this.variant}` : ''
            ]
        }
    },
    methods:{
        onClick(){
            this.$emit('close')
        },
    }
}
</script>

<style scoped>
.alert {
    display: flex;
    justify-content: space-between;
    background-color: gray;
    padding: 5px;
    border-radius: 6px;
    color: aqua;
}

.alert-success {
    background-color: green;
    color: white;
}

.alert-danger {
    background-color: red;
    color: white;
}
</style>