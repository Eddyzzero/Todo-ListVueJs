<template>

  <header class="flex flex-col items-center pt-40 bg-amber-200">
    <h1 class=" text-2xl uppercase">check Norris</h1>
    <p> parce que tes tâches ne survivent pas longtemps!</p>
  </header>
  <hr class="border-cyan-50/40 my-4">
  <main>

    <section class="flex justify-center gap-5 m-5 text-amber-100">
      <input
      class="p-2 border border-cyan-50/40 rounded-lg"
      type="text" 
      placeholder="Ajoutez une tâche"
      @submit="addTask"
      v-model="tasksName">
      <button @click="addTask" class=" text-amber-100 text-2xl"> + </button>
    </section>

    <section class=" text-amber-50">
      <ul class=" flex flex-col gap-5 m-5">
        <li class=" flex gap-2 justify-between border rounded px-3 py-5 hover:opacity-50" v-for="task in tasks" :key="task">
          <div class="flex gap-2 items-center">
            <input type="checkbox" class="cursor-pointer accent-amber-200">
            <p> {{ task }}</p>
          </div>
          <i class="fa-solid fa-trash cursor-pointer leading-none" style="color: #FFD43B;"
          @click="deleteTask(task)"></i>
        </li>
      </ul>
    </section>

  </main>

</template>

<script setup>
import { ref } from 'vue'

const tasks = ref([]); // Tableau de tâches
const tasksName = ref(""); // Nom de la tâche

const deleteTask = (task) => {
  tasks.value = tasks.value.filter(t => t !== task)
}
const addTask = (event) => {
  event.preventDefault();
  tasks.value.push(tasksName.value)
  tasksName.value = "";
}
</script>