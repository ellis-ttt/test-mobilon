<script setup lang="ts">
defineProps<{
  messages: Array<Message>
  currentUser: User
}>()
</script>

<template>
  <div class="message-list">
    <div
      v-for="message in messages"
      :key="message.timestamp"
      :class="{ 'own-message': message.user === currentUser }"
    >
      {{ `${message.user.name}: ${message.text}` }}
    </div>
  </div>
</template>
