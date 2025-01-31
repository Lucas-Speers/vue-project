<script setup lang="ts">
import { ref, defineExpose } from 'vue';
const emit = defineEmits(['submitModal'])

const text = ref('')
const showingModal = ref(false)

function submitModal() {
	emit('submitModal', text.value)
	text.value = ''
	showingModal.value = false
}

defineExpose({showingModal})
</script>

<template>
	<div v-if="showingModal" class="modal-backdrop" @click="showingModal=false">
		<div class="modal" @click.stop="">
			<slot>Default Modal</slot>

      <button @click="showingModal=false">❌</button>

			<form @submit.prevent="submitModal()">
				<input v-model="text">
			</form>

		</div>
	</div>
</template>

<style>
	/* IDK how this works */
  .modal-backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    flex-direction: column;
  }
</style>
