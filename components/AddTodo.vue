<template>
  <input type="text" v-model="newItem" @input="listSuggest" />
  <CommonAppBaseButton
    text="Add"
    :class="{ btn: true }"
    @action="onSubmitAddItem"
  />
  <CommonAppBaseButton
    text="Search"
    :class="{ btn: true }"
    @action="onSubmitSearchItem"
  />
</template>

<script setup>
import { v4 as uuidv4 } from "uuid";
const newItem = ref("");
const emit = defineEmits(["add-item", "search-value", "suggest-list"]);

const onSubmitAddItem = () => {
  const itemChild = {
    id: uuidv4(),
    title: newItem.value,
    completed: false,
  };
  emit("add-item", itemChild);
  newItem.value = "";
};

const onSubmitSearchItem = () => {
  emit("search-value", newItem.value);
};
const listSuggest = () => {
  emit('suggest-list', newItem.value)
};
</script>

<style lang="scss" scoped>
@mixin btn-add {
  background: #32cc53;
  margin: 0;
  padding: 0;
}
.btn-default {
  @include btn-add;
}
.btn {
  @extend .btn-default;
}
</style>    