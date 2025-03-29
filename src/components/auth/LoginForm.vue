<script setup>
import { reactive, toRaw } from 'vue'
import FormContainer from './FormContainer.vue'
import IButton from 'components/ui/IButton.vue'
import IInput from 'components/ui/IInput.vue'

const emit = defineEmits(['submit'])

const userData = reactive({
  email: '',
  password: '',
})
</script>

<template>
  <FormContainer @submit.prevent="emit('submit', toRaw(userData))">
    <div class="flex w-full flex-col gap-4.5">
      <IInput label="Email" placeholder="Enter your email address" v-model="userData.email" />
      <IInput
        label="Password"
        type="password"
        placeholder="Enter your password"
        v-model="userData.password"
      />
    </div>

    <IButton variant="gradient" type="submit">Sing In</IButton>
  </FormContainer>
</template>
