<template>
    <!-- <div :class="['alert', {'alert-success': variant==='success',
    'alert-danger': variant==='danger'}]">
        Seu formulario foi enviado com sucesso!
    </div> -->
    <br><br>
    <div :class="baseClass">
        {{ test }}
        <slot />
    </div>
</template>

<script>
export default {
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
}
</script>

<style scoped>
.alert {
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