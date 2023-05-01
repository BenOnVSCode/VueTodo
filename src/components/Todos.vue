<script setup>
import { ref } from 'vue';


const todo = ref("")
const todos = ref([
    {
        value: "TASK1",
        open: false
    }
    , 
    {
        value: "TASK2",
        open: false
    }
    , 
    {
        value: "TASK3",
        open: false
    }
])
// watch(
//     todos, 
//     () => {
//         console.log(todos.value)
//     },
//     {
//         deep:true
//     }
// )

function addTodo(){
    if(todo.value !== ""){
        todos.value.push({value:todo.value, open: false})
        todo.value = ""
    }
    
}

function deleteTodo(index){
    todos.value.splice(index, 1)
}
function openUpdate(updatedIndex){
    todos.value = todos.value.map((val, index) => {
        if(index === updatedIndex){
            return {
                ...val,
                open:true
            }
        }
        return val
    })
}
function updateTodo(updatedIndex){
    todos.value = todos.value.map((val, index) => {
        if(index === updatedIndex){
            return {
                ...val,
                open: false
            }
        }
        return val
    })
}
</script>

<template>
    <div class="flex-column gap-3">
        <div class="flex my-5">
            <input class="outline-none" type="text" v-model="todo" placeholder="Write a todo"/>
            <button class="text-white bg-red-500 w-48 h-10 cursor-pointer font-bold "  @click="addTodo">ADD</button>
        </div>
        <div class="flex flex-col gap-5">
            <div class="flex-row" v-for="(item, index) in todos" :key="index">
                <h1 v-if="!item.open" class="text-white font-bold text-lg flex">{{item.value}}</h1>
                <input v-if="item.open" v-model="item.value" class="outline-none h-10" />
                <button class="bg-purple-500  hover:bg-purple-50 text-white font-bold py-2 px-4 rounded cursor-pointer" v-if="item.open" @click="updateTodo(index)">Update</button>
                <div class="flex gap-2">
                    <button v-if="!item.open" class="bg-red-500 hover:bg-red-400 text-white font-bold py-2 px-4 rounded cursor-pointer"  @click="deleteTodo(index)">
                        Delete
                    </button>
                    <button v-if="!item.open"  class="bg-purple-800 hover:bg-purple-400 text-white font-bold py-2 px-4 rounded cursor-pointer" @click="openUpdate(index)">
                        Update
                    </button>
                </div>
            </div>
            
        </div>
    </div>
    
</template>


<style scoped>
</style>
