<script setup>
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
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
          <TodoInput />
          <TodoList/>
        </div>
      </div>
    </div>
  </div>
</div>

</template>

<style scoped>

</style>
