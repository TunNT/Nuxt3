<template>
  <input
    type="text"
    v-model="val"
    @input="handleInput"
  />
</template>

<script setup>
import { onMounted } from 'vue'
const props = defineProps({
    value: {
    type: String,
    default: "",
  },
});
onMounted(()=> {
    val.value = props.value
})
const val = ref(null)
const emit = defineEmits(["check-value"]);
const handleInput = () => {
    emit('check-value', val.value);
    val.value = ''
}
</script>

<style>
</style>