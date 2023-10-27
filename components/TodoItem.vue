<template>
  <p :class="['todo-item', item.completed ? 'is-completed' : '']">
    <input
      type="checkbox"
      :checked="item.completed"
      @change="markItemCompleted"
    />
    {{ item.title }}
    <!-- <button class="del-btn-edit" @click="onDialog">Edit</button> -->
    <commonAppBaseButton
      :text="text"
      :class="{'del-btn-del' : true }"
      @action="onSubmitDelete"
    />
  </p>
</template>

<script setup>
const props = defineProps({
  item: {
    type: Object,
    default: () => {},
  },
});
const onCancelEditHandler = () => {};
const onSubmitEditHandler = () => {};

const selectItem = ref({});
const text = ref("Delete");

const emit = defineEmits(["change-compeleted", "delete-item"]);

const markItemCompleted = () => {
  emit("change-compeleted", props.item.id);
};

const onSubmitDelete = () => {
  emit("delete-item", props.item.id);
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  margin: 0;
  border-bottom: 1px #ccc dotted;
}
.is-completed {
  text-decoration: line-through;
}
.del-btn-edit {
  background: green;
  color: #fff;
  border: none;
  cursor: pointer;
  float: right;
}
.del-btn-del {
  background: #ff0000;
  color: #fff;
  border: none;
  cursor: pointer;
  float: right;
}
</style>