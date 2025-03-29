<script setup>
import { reactive, toRaw } from 'vue'
import IButton from 'components/ui/IButton.vue'
import IInput from 'components/ui/IInput.vue'
import FormContainer from './FormContainer.vue'

const emit = defineEmits(['submit'])

const userData = reactive({
  name: '',
  email: '',
  password: '',
})
</script>

<template>
  <FormContainer @submit.prevent="emit('submit', toRaw(userData))">
    <div class="flex w-full flex-col gap-4.5">
      <IInput label="Full name" placeholder="Enter your full name" v-model="userData.name" />
      <IInput
        label="Email"
        type="password"
        placeholder="Enter your email address"
        v-model="userData.email"
      />
      <IInput
        label="Password"
        type="password"
        placeholder="Create a strong password"
        v-model="userData.password"
      />
    </div>

    <IButton variant="gradient" type="submit">Create account</IButton>
  </FormContainer>
</template>
