<template>
  <button
    :class="{className : isValid }"
    @click="onSubmit"
  >
    {{ text }}
  </button>
</template>

<script setup>

const props = defineProps({
  width: {
    type: [String, Number],
    default: undefined,
  },
  isValid : {
    type: Boolean,
    default: false,
  },
  text: {
    type: String,
    default: "",
  },
  className: {
    type: String,
    default: "",
  },
});
const emit = defineEmits(['action']);
const onSubmit = () => {
    emit('action');
}
</script>

<style>
</style>