<script setup lang="ts">
import { ref } from 'vue';
import Task from './components/Task.vue'
import Modal from './components/Modal.vue'

const addTaskModel = ref(null)
const editTaskModel = ref(null)

const editingId = null

let id = 0
const tasks = ref([])

function addTask(name) {
	tasks.value.push({id: id++, name: name})
}

function editTask(taskId, name) {
	tasks.value.forEach((t, i) => {if (t.id == taskId) {t.name = name}})
}

function removeTask(taskId) {
	tasks.value = tasks.value.filter((t) => t.id !== taskId)
}
</script>

<template>
	<h1>Todo App</h1>
	
	<button @click="addTaskModel.showingModal=true">Add</button>
	<Modal ref="addTaskModel" @submitModal="(t) => addTask(t)">Add Task</Modal>

	<Modal ref="editTaskModel" @submitModal="(t) => editTask(editingId, t)">Edit Task</Modal>

	<ul v-for="task in tasks" :id="task.id">
		<li>
			<Task :taskName="task.name" :taskId="task.id" @remove="removeTask(task.id)" @edit="editTaskModel.showingModal=true;editingId=task.id" />
		</li>
	</ul>
</template>
