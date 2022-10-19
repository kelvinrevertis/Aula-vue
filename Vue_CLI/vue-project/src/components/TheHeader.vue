<template>

    <div>
        <h1 :class=classVar>
            Curso Vue3
        </h1>

        <h1 :class="{title: true, 'title-home': isHome}">
            Testando Curso Vue3
        </h1>

        <p :class="['text',{'title-home': isHome}]">
            Lorem ipsum dolor sit amet consectetur adipisicing elit.
        </p>

        <p :style="styleClass">
            Lorem ipsum dolor sit amet consectetur adipisicing elit.
        </p>

        <div>

            Two-way data binding
            v-model -> formularios
            <br><br>

            <label for="">Nome</label> <br>
            <input v-model="name" type="text"><!-- sincronizado -->
            {{name}}
        </div>
        <br>

        <label for="">Esportes</label>
        <select v-model="sports">
            <option value="">Escolha</option>
            <option value="futebol">Futebol</option>
            <option value="skate">Skate</option>
            <option value="tenis">Tenis</option>
        </select><br>
        {{sports}}
        <br><br>
        <div>
            <label>Newsletter</label><br>
            <input v-model="newsletter" type="radio" value="sim">Sim
            <input v-model="newsletter" type="radio" value="nao">Não
            <br>{{newsletter}}
        </div>

        <br><br>

        <div>
            <label>Cores que você mais gosta</label> <br>
            <input v-model="colors" type="checkbox" value="azul">Azul <br>
            <input v-model="colors" type="checkbox" value="amarelo">Amarelo <br>
            {{colors}}
        </div>


        <br><br>

        <label>Contrato</label><br>
        <input v-model="contract" type="checkbox" value="sim">Aceita o termos?
        <br>{{contract}}

        <br>
        <br>


        <div>
            <button v-on:click="onClick()">
                Enviar
            </button>
        </div>

        <div>
            <button @click="onClick">
                Enviar2
            </button>
        </div>

        <div @mouseover="onMouseOver()" @mouseout="onMouseOut">
            Mouse Over
        </div>

        <form action="https://www.google.com.br/" @submit="onSubmit">
            <button type="submit">
                Enviar Submit
            </button>
        </form>

        <form action="https://www.google.com.br/" @submit.prevent="onSubmitPrevent">
            <button type="submit">
                Submit Prevent
            </button>
        </form>


        <button @click.once="onClickOnce">
            Enviar Once
        </button>
        <button @click.stop="onClickStop">
            Enviar Stop
        </button>
        <button @click.self="onClickSelf">
            Enviar Self
        </button>
        <button @click.capture="onClickCapture">
            Enviar Capture
        </button>
        <button @click.passive="onClickPassive">
            Enviar Passive
        </button>

        <div>
            <input type="text" @keyup="onKeyUp">
        </div>
        <div>
            <input type="text" @keyup.enter="onKeyUpEnter">
        </div>

        https://vuejs.org/guide/essentials/event-handling.html#event-modifiers



        <br><br>
        <img v-bind:src="imgSrc" v-bind:alt="imgAlt">

        <header class="header">
            Header
        </header>

        <div v-for="(obj, index) in todos" v-bind:key="obj.id" class="todos-item">

            <img v-if="obj.imgSrc" :src="obj.imgSrc" v-bind:alt="obj.imgAlt">
            {{ index }} - {{obj.title}}

        </div>

        <section></section>
    </div>

</template>

<script>
import { computed } from '@vue/reactivity'

export default {
    name: 'App',
    data() {
        return {
            colors: [],
            contract: false,
            newsletter: "",
            sports: '',
            name: 'Kelvin R',
            styleClass: { color: 'aqua', 'backgroundColor': 'green' },
            isHome: true,
            imgSrc: 'https://via.placeholder.com/150',
            imgAlt: 'Foto de Jon Snow',
            classVar: 'title',
            todos: [
                {
                    "imgSrc": 'https://via.placeholder.com/150',
                    "imgAlt": 'Foto de Jon Snow',
                    "userId": 1,
                    "id": 1,
                    "title": "delectus aut autem",
                    "completed": false
                },
                {
                    "imgSrc": 'https://via.placeholder.com/150',
                    "userId": 1,
                    "id": 2,
                    "title": "quis ut nam facilis et officia qui",
                    "completed": false
                },
                {
                    "userId": 1,
                    "id": 3,
                    "title": "fugiat veniam minus",
                    "completed": false
                },
                {
                    "userId": 1,
                    "id": 4,
                    "title": "et porro tempora",
                    "completed": true
                },
                {
                    "userId": 1,
                    "id": 5,
                    "title": "laboriosam mollitia et enim quasi adipisci quia provident illum",
                    "completed": false
                }
            ]
        }
    },
    methods: {
        onClick($evt) {
            console.log('click', $evt)
        },
        onMouseOver() {
            console.log('mouse over')
        },
        onMouseOut($evt) {
            console.log('mouse out', $evt)
        },
        onSubmit($evt) {
            console.log('on Submit', $evt)
        },
        onSubmitPrevent() {
            console.log('on Submit Prevent')
        },
        onClickOnce() {
            console.log('on Submit Once')
        },
        onClickStop() {
            console.log('on Click Stop')
        },
        onClickSelf() {
            console.log('on Click Self')
        },
        onClickCapture() {
            console.log('on Click Capture')
        },
        onClickPassive() {
            console.log('on Click Passive')
        },
        onKeyUp(evento) {
            console.log(evento.key)
        },
        onKeyUpEnter(evento) {
            console.log(evento)
        }
    },
    methods: {

    },

}

</script>

<style>
.title-home {
    font-size: 40px;
    color: green;
}

.text {
    color: yellow;
}

.title {
    font-size: 20px;
    color: blue;
    background-color: grey;
}

.todos-item {
    background-color: #FFF;
    margin: 0 0 5px 0;
    padding: 3px 6px;
    color: #fff;
    color: #000;
}

.header {

    background: #000;
    color: #FFF;
}
</style>