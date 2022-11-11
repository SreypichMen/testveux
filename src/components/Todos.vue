<template>
    <div>
        <h3>
            Todos
           
        </h3>
        <div class="todos">
            <div v-for="todo in allTodos" v-bind:key="todo.id" class="todo">
                    {{todo.title}}

                  <button @click= "deleteTodo(todo.id)" style="background-color: red; color: white; cursor: pointer;">Delete</button>
            </div>
          </div>
    </div>
</template>
<script>
import {mapGetters,mapActions} from 'vuex'
export default {
    name: "To-dos",
    methods:{
        ...mapActions(['fetchTodos', 'deleteTodo']),
        
},
    computed : mapGetters(['allTodos']),
    created(){
        this.fetchTodos();
    }
}

</script>
<style scoped>
.todos{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
}
.todo{

    border: 1px solid #ccc;
    background-color: #41b883;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;

}
button{
    position: absolute;
    bottom: 10px;
    right: 10px;
    color: white;
    cursor: pointer;
}
</style>



