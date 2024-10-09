<script setup lang="ts">
import { ref } from 'vue'

let props = defineProps<{
    user: User
}>()
let emit = defineEmits<{
    (e: 'send', id: string): void
}>()

let messageText = ref('')

function sendMessage() {
    if (messageText.value.trim()) {
        emit('send', messageText.value)
        messageText.value = ''
    }
}
</script>

<template>
    <div class="message-input">
        <input v-model="messageText" @keyup.enter="sendMessage" />
        <button @click="sendMessage">Send</button>
    </div>
</template>
