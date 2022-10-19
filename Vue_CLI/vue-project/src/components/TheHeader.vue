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

        <select v-model="sports">
            <option value="futebol">Futebol</option>
            <option value="skate">Skate</option>
            <option value="tenis">Tenis</option>
        </select>


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
export default {
    name: 'App',
    data() {
        return {
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
    }
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