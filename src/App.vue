<script setup lang="ts">
import { ref } from 'vue'
import ChatWindow from './components/ChatWindow.vue'

let messages = ref([] as Array<Message>)

function sendMessage(text: string, user: User) {
  messages.value.unshift({ text, user, timestamp: Date.now() })
}
</script>

<template>
  <div class="app">
    <ChatWindow :messages="messages" :user="{ name: 'Alice' }" @send-message="sendMessage" />
    <ChatWindow :messages="messages" :user="{ name: 'Bob' }" @send-message="sendMessage" />
  </div>
</template>
