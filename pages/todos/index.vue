<template>
  <AddTodo
    @add-item="onSubmitAddItem"
    @search-value="onSubmitSearchItem"
    @suggest-list="onSuggestList"
  />
  <TodoItem
    v-for="todo in todos"
    :key="todo.id"
    :item="todo"
    @change-compeleted="markItemCompleted"
    @delete-item="onSubmitDelete"
  />
</template>

<script>
import { ref } from "vue";
import axios from "axios";
export default {
  setup() {
    const todos = ref();
    const getAllData = async () => {
      try {
        const data = [
          {
            userId: 1,
            id: 1,
            title: "delectus aut autem",
            completed: false,
          },
          {
            userId: 1,
            id: 2,
            title: "quis ut nam facilis et officia qui",
            completed: false,
          },
          {
            userId: 1,
            id: 3,
            title: "fugiat veniam minus",
            completed: false,
          },
          {
            userId: 1,
            id: 4,
            title: "et porro tempora",
            completed: true,
          },
          {
            userId: 1,
            id: 5,
            title:
              "laboriosam mollitia et enim quasi adipisci quia provident illum",
            completed: false,
          },
        ];
        // const { data } = await axios.get(
        //   "https://jsonplaceholder.typicode.com/todos?_limit=5"
        // );
        todos.value = data;
      } catch (err) {
        console.log(err);
      }
    };
    getAllData();

    const markItemCompleted = (id) => {
      todos.value = todos.value.map((item) => {
        if (item.id === id) {
          item.completed = !item.completed;
        }
        return item;
      });
    };
    const onSubmitDelete = (id) => {
      todos.value = todos.value.filter((item) => {
        if (item.id !== id) {
          return item;
        }
      });
    };
    const onSubmitAddItem = async (item) => {
      try {
        if (item.title.length === 0) {
          alert("Plz enter new value");
        } else {
          //   const { data } = await axios.post(
          //     "https://jsonplaceholder.typicode.com/todos",
          //     item
          //   );
          getAllData();
          todos.value.push(item);
        }
      } catch (err) {
        console.log(err);
      }
    };

    const onSubmitSearchItem = (item) => {
      const results = todos.value.map((todo) => {
        if (todo.title.includes(item)) {
          return todo;
        }
      });
      todos.value = results.filter((item) => item !== undefined);
    };

    const onSuggestList = (item) => {
      if (item.length !== 0) {
        getAllData();
        const results = todos.value.map((todo) => {
          if (todo.title.includes(item)) {
            return todo;
          }
        });
        todos.value = results.filter((item) => item !== undefined);
      } else {
        getAllData();
      }
    };

    return {
      todos,
      getAllData,
      markItemCompleted,
      onSubmitDelete,
      onSubmitAddItem,
      onSubmitSearchItem,
      onSuggestList,
    };
  },
};
</script>

<style>
</style>