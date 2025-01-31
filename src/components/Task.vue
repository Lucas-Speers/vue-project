<script setup lang="ts">
const props = defineProps(['taskName'])
const emit = defineEmits(['remove', 'edit'])
</script>

<template>
	<button @click="emit('remove')">❌</button>
	<button @click="emit('edit')">✏️</button>
	<span>{{ taskName || '`taskName` not defined' }}</span>
</template>