<template>
    <section class="todoapp">
<header class="header">

    <h1>Todos</h1>
    

    <input type="text" class="new-todo" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter="addTodo">

</header>

<div class="main">

    <input type="checkbox" class="toggle-all" v-model="allDone"> <!-- n'apparait pas, présent dasn el DOM mais ne se voit pas et l'intéraction est impossible -->

    <ul class="todo-list">

        <li class="todo" v-for="todo in filteredTodos" :key="todo.id" :class="{completed: todo.completed}"> <!-- :key="todo.id ne sert à rien, mais si il est absent vsc m'inscris une erreur -->

            <div class="view">

                <input type="checkbox" v-model="todo.completed" class="toggle">

                <label>{{ todo.name }}</label>

                <button class="destroy" @click.prevent="deleteTodo(todo)"></button>

            </div>

        </li>
    </ul>
</div>

<footer class="footer">
    <span class="todo-count"><strong>{{ remaining }}</strong> tâches à faire</span> <!--compteur-->

    <ul class="filters">
        <li><a href="#" :class="{selected: filter === 'all'}" @click.prevent="filter ='all'">Toutes</a></li>
        <li><a href="#" :class="{selected: filter === 'todo'}" @click.prevent="filter ='todo'">A faire</a></li>
        <li><a href="#" :class="{selected: filter === 'done'}" @click.prevent="filter ='done'">Faites</a></li>
    </ul>

</footer>

    </section>
</template>

<script>


export default {
    data () {
        return {

            todos: [{
                name:'Tâche de test',
                completed: false
            }],

            newTodo: '',
            filter: 'all'
        }
    },

    methods: {

        //ajoute, supprime une tache
        addTodo () { //lié input ligne 7
            this.todos.push({
                completed: false,
                name: this.newTodo
            })
            this.newTodo = ''
        },
        deleteTodo () { //lié button ligne 26
            this.todo = this.todo.filter(i => i !== todo)
        }
        
    },

    computed: {

        //relié a l'input qui ne s'affiche pas, il sert à coché la totalité des taches
        allDone: {
            get () {
                return this.remaining === 0
            },

            set (value) {
                this.todo.forEach(todo => {
                    todocompleted = value
                })
            }
        },

        //compteur
        remaining () {
            return this.todos.filter(todo => !todo.completed).length
        },

        //système de filtre relié ligne 18 et avec la liste ligne 37
        filteredTodos () {

            //Ce if else bloque toutes les fonctionnalités. Si je le commente en laissant le "return this.todos" 
            //j'en retrouve certaines mais ça ne fonctionne pas comme ça devrait
            

            if (this.filter === 'todo') {
                return this.todos(todo => !todo.completed)

            } else if (this.filter === 'done') {
                return this.todos(todo => todo.completed)

            } 
            return this.todos   
            
        }
    }
        
}
</script>

<style src="./todos.css">

</style>
