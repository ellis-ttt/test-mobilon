<script setup lang="ts">
defineProps<{
  messages: Array<Message>
  currentUser: User
}>()
</script>

<template>
  <div class="message-list">
    <div
      v-for="message in [...messages].reverse()"
      :key="message.timestamp"
      :class="{ 'own-message': message.user.name === currentUser.name }"
      class="message"
    >
      {{ `${message.user.name}: ${message.text}` }}
    </div>
  </div>
</template>

<style scoped>
.message {
  border-radius: 0.5rem;
  padding: 0.5rem;
  margin: 0.5rem 0;
  background: linear-gradient(to bottom, red, blue);
}

.own-message {
  background: linear-gradient(to bottom, green, purple);

  text-align: right;
}
</style>
