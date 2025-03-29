<script setup>
const props = defineProps({
  modelValue: String,
  label: String,
  placeholder: String,
  type: {
    default: 'text',
    type: String,
  },
})

defineOptions({
  inheritAttrs: false,
})

defineEmits(['update:modelValue'])

const baseStyles =
  'focus:border-accent w-full rounded-sm border border-solid border-black/10 bg-inherit px-4.5 py-3.5 text-sm font-normal transition-all duration-200 ease-in outline-none placeholder:text-black/50 dark:border-white/10 dark:placeholder:text-white/50'
</script>

<template>
  <label class="h-max w-full">
    <span class="mb-2 block px-4 text-xs font-normal">{{ props.label }}</span>
    <component
      :is="type === 'textarea' ? 'textarea' : 'input'"
      :class="`${baseStyles} ${type === 'textarea' ? 'resize-none' : ''}`"
      v-bind="{ ...$props, ...$attrs }"
      :placeholder="placeholder"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </label>
</template>
