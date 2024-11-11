<script setup>
import { ref } from 'vue';
import { onMounted } from 'vue';

const localStoragevalue = ref("")
const storedValue = ref("")


onMounted(() => {
  const value = localStorage.getItem('todoList');
  if (value) {
    storedValue.value = JSON.parse(value) 
  } else {
    storedValue.value = 'No data found in localStorage.';
  }
});
</script>

<template>

    <div class="">
        <!-- <ul style="list-style: none;">
            <li>{{ value }}</li>
        </ul> -->

        <p v-if="storedValue">{{ storedValue }}</p>
    <p v-else>No data found in localStorage.</p>
    </div>



</template>


<style scoped></style>