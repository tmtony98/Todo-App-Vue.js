<script setup lang="ts">
import {onMounted, ref} from 'vue';
import axios from "axios";


const inputvalue = ref<string>("")
const todoList = ref<string[]>([])

// const emit = defineEmits(['inFocus', 'submit'])

const emit = defineEmits<{
  (event: 'submit', inputvalue: string): void
}>()

watch(inputvalue, (newX) => {
  console.log(`inputvalue ${newX}`)
})

// const submit = (e) => {
//     e.preventDefault()
//     todoList.value.push(inputvalue.value)
//     localStorage.setItem("todoList", JSON.stringify(todoList.value))
//     //  sendData()
//     inputvalue.value = ''
// }

const sendData = async () => {
    const res = await  axios.post("http://localhost:3000/tasks",  {
    task: "This is the new task for ID d44c"
})
    console.log(res)
}

onMounted(() => {
    const storedTodoList = localStorage.getItem("todoList")
    if (storedTodoList) {
        todoList.value = JSON.parse(storedTodoList)
    }
})
</script>


<template>

    <form>
        <div class="mb-3 ">
            <label class="form-label" for="exampleInput">Add new Todo</label>
            <div class="d-flex">
                <input id="exampleInput" v-model="inputvalue" aria-describedby="emailHelp" class="form-control"
                       placeholder="Add new" type="text">
                <button class="btn btn-primary mx-2  " @click.prevent="emit('submit',inputvalue)">Add</button>
            </div>
            <!--            <ul v-for="list in todoList">-->
            <!--                <li>{{ list }}</li>-->
            <!--            </ul>-->
        </div>
    </form>

</template>


<style scoped></style>
