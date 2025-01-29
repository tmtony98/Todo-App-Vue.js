<script setup lang="ts">
import { computed } from "vue";
import { onMounted, ref, watch } from 'vue';
import axios from "axios";
import { Users } from "./interfaces";

interface User {
    name: string;
    id: number;
    email: string;
    phone: number
}

const usersList = ref<User[]>([]);
const user = ref<string>("");




onMounted(() => {
    const getUserList = async () => {
        try {
            const response = await axios.get<User[]>('https://jsonplaceholder.typicode.com/users');
            console.log("res", response.data);
            usersList.value = response.data;
        } catch (error) {
            console.error(error);
        }
    }
    getUserList();
});


const filteredUsers = computed(() =>
    usersList.value.filter(item => item.name.toLowerCase().includes(user.value.toLowerCase()))
);


</script>

<template>

    <div class="d-flex justify-content-center">
        <div class="card w-50">
            <div class="card-body">
                <h1 class="card-title m-3">User List</h1>
                <label for="search" class="form-label">Search</label>
                <input type="text" id="search" v-model="user" class="form-control" placeholder="Search user" />
                <button @click="getUserList">Refresh</button>
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">User id</th>
                            <th scope="col">User Name</th>
                            <th scope="col">Email</th>
                            <th scope="col">Phone No</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="user in filteredUsers" :key="user.id">
                            <td>{{ user.id }}</td>
                            <td>{{ user.name }}</td>
                            <td>{{ user.email }}</td>
                            <td>{{ user.phone }}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
