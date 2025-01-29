<script setup lang="ts">
const props = defineProps(['taskName', 'taskId'])
const emit = defineEmits(['remove'])
</script>

<template>
	<button @click="emit('remove', taskId)">X</button>
	<span>{{ taskName || '`taskName` not defined' }}</span>
</template>