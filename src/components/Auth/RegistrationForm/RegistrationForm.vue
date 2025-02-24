<script setup>
import IButton from '@/components/IButton/IButton.vue'
import IInput from '@/components/IInput/IInput.vue'

const emit = defineEmits(['submit'])
</script>

<template>
  <form
    @submit.prevent="emit('submit', { name: 'NAme' })"
    class="max-w-[499px] w-full p-10 rounded-2xl"
  >
    <IInput class="mb-4.5" label="Full name" placeholder="Enter your full name" />
    <IInput class="mb-4.5" label="Email" placeholder="Enter your email address" />
    <IInput class="mb-10" label="Password" type="password" placeholder="Create a strong password" />
    <IButton variant="primary" type="submit">Create account</IButton>
  </form>
</template>
