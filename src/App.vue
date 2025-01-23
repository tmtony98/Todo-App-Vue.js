<script setup>
import TodoInput from './components/TodoInput.vue';
import TodoList from "./components/TodoList.vue";
import {ref} from "vue";
// The value received from the child
const receivedValue = ref("");

const handleValue = (value) => {
    receivedValue.value = value;
    console.log("Received value from child:", receivedValue.value);
};

function todo(value) {
    console.log("Received value from child:", value );
}


</script>

<template>
    <div class="container">
        <div class="row d-flex justify-content-center align-items-center ">
            <div class="col-lg-6  col-md-12 col-12">
                <div class="card mt-5">
                    <div class="card-header">
                        <h3 class="text-primary"> To Do app</h3>
                    </div>
                    <div class="card-body">
                        <TodoInput  @someEvent="todo"/>
                        <TodoList @send-value="handleValue"/>
                        <p>{{receivedValue}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped>

</style>
