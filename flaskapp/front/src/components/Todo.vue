<template>
  <div class="container">
    <b-form @submit.stop.prevent>
      <label for="todo-item">Todo</label>
      <b-input v-model="todoItem" name="todo-item" type="text"></b-input>
      <b-button @click="insertItem" class="m-2 float-right">Adicionar</b-button>
    </b-form>
    <b-table striped hover :items="items"></b-table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      todoItem: "",
      items: [{ id: 0, todo: "" }],
    };
  },
  created() {
    this.getList()
  },
  methods: {
    insertItem(){
      axios.post("http://localhost:8181/todo", {
        "todo": this.todoItem
      }).then(() => {
        this.getList()
      })
    },
    getList() {
      axios.get("http://localhost:8181/todo").then((response) => {
      this.items = response.data.data;
    });
    }
  }
};
</script>
<style scoped>
  .container {
    margin-top: 5%;
    width: 50%;
  }
</style>