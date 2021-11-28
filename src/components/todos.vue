<template>
    <section class="todoapp">
        <header class="header">
            <h1 >Todos</h1>
            <input type="text" class="new-todo" placeholder="Ajouter une tache" v-model="newTodo" @keyup.enter="addTodo">
        </header>
            <div class="main">
                <ul class="todo-list">
                    <li class="todo" v-for="todo in todos" v-bind:key="todo" v-bind:class="{completed: todo.completed}">
                        <div class="view">
                            <input type="checkbox" v-model="todo.completed" class="toggle">
                            <label >{{todo.name}}</label>
                        </div>
                    </li>

                </ul>

            </div>
            <footer class="futter">
                    <span class="todo-count"><strong>{{remaining}}</strong>Tache à faire</span>
            </footer>
    </section>
</template>



<script>
export default {
        data(){
            return{
                todos : [{ 
                    name :'tache de test',
                    completed : false
                }],
                newTodo : ''
            }
        },
        methods : {
            addTodo(){
                this.todos.push({
                    completed : false,
                    name : this.newTodo
                })
                this.newTodo = ''
            }
        },

        completed :{
            remaining(){
               return this.todos.filter((todo)=>{
                   return !todo.completed
               }).length
            }
        }
}
</script>

<style src="./todos.css">

</style>