<script setup>
import { computed, ref } from 'vue';


const inputvalue = ref("")



    const submit = (e) => {
        e.preventDefault()
        localStorage.setItem("todoList", JSON.stringify(inputvalue))
        console.log("btn clicked");
    }


</script>


<template>

    <form>
        <div class="mb-3 ">
            <label for="exampleInput" class="form-label">Add new Todo</label>
            <div class="d-flex">
                <input type="text" v-model="inputvalue" class="form-control" id="exampleInput"
                    aria-describedby="emailHelp">
                <button @click="submit" class="btn btn-primary mx-2  ">Add</button>
            </div>
            <!-- <p>{{ inputvalue }}</p> -->
          
        </div>
    </form>

</template>


<style scoped></style>