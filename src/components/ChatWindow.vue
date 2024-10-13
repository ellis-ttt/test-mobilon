<script setup lang="ts">
import MessageList from './MessageList.vue'
import MessageInput from './MessageInput.vue'

let props = defineProps<{
  messages: Array<Message>
  user: User
}>()

let emit = defineEmits<{
  (e: 'sendMessage', text: string, user: User): void
}>()

function sendMessage(text: string) {
  emit('sendMessage', text, props.user)
}
</script>

<template>
  <div class="chat-window">
    <MessageList :messages="messages" :currentUser="user" />
    <MessageInput :user="user" @send="sendMessage" />
  </div>
</template>

<style scoped>
div {
  padding: 1rem;
}
</style>
