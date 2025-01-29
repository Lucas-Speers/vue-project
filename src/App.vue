<script setup lang="ts">
import { ref } from 'vue';
import Task from './components/Task.vue'
import Modal from './components/Modal.vue'

const modalRef = ref(null)

let id = 0
const tasks = ref([
	{ id: id++, name: 'eat food' },
	{ id: id++, name: 'eat cat' },
	{ id: id++, name: 'perish' }
])

function addTask(name) {
	tasks.value.push({id: id++, name: name})
}

function removeTask(taskId) {
	tasks.value = tasks.value.filter((t) => t.id !== taskId)
}
</script>

<template>
	<h1>Todo App</h1>
	<button @click="modalRef.showingModal=true">Add</button>
	<Modal ref="modalRef" @add="(t) => addTask(t)" />
	<ul v-for="task in tasks" :id="task.id">
		<li>
			<Task :taskName="task.name" :taskId="task.id" @remove="(id) => removeTask(id)" />
		</li>
	</ul>
</template>
