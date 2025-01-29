<script setup lang="ts">
import { ref } from 'vue';
const emit = defineEmits(['add'])

const newTask = ref('')

function addTask() {
	emit('add', newTask.value)
	newTask.value = ''
}
</script>

<template>
	<form @submit.prevent="addTask()">
		<input v-model="newTask">
	</form>
</template>