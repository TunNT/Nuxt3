<template>
  <form>
    <BaseInput :value="check" @check-value ="onSubmit"/>
    <button @click="onSubmitValue"> Add</button>
  </form>
</template>

<script setup>
const check = ref('');
const items = ref({a:111,item:{
  name: "Trung",
  age: 24,
  sex: "male",
}});
const item = reactive();

const props = defineProps({
  name: {
    type: Array,
    default: () => [],
  },
  isDisabled: {
    type: Boolean,
    default: false,
  },
});

const newValue = ref('');
const emit = defineEmits(["submit-elemment"]);

const onSubmitValue = ($event) => {
    emit('submit-elemment', newValue.value);
    newValue.value = ''
    $event.preventDefault()
}
const onSubmit = (item) =>{
    newValue.value = item
}
</script>

<style>
</style>