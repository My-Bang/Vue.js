<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoList from './components/TodoList.vue';
import TodoInput from './components/TodoInput.vue';

export default {
  components: {
    TodoHeader,
    TodoList,
    TodoInput,
  },
  data() {
    return {
      todos: [],
      currentTab: 'all',
      nextId: 1,
    };
  },
  computed: {
    computedTodo() {
      if (this.currentTab === 'all') return this.todos;
      else return this.todos.filter(todo => todo.completed);
    },
  },
  methods: {
    addTodo(msg) {
      if (!msg.trim()) return;
      this.todos.push({ id: this.nextId++, msg, completed: false });
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    updateTodo(id) {
      const todo = this.todos.find(todo => todo.id === id);
      if (todo) todo.completed = !todo.completed;
    },
    updateTab(tab) {
      this.currentTab = tab;
    },
  },
};
</script>

<template>
  <div class="todo">
    <TodoHeader :current="currentTab" @update-tab="updateTab" />
    <TodoList
      :computedTodo="computedTodo"
      @delete-todo="deleteTodo"
      @update-todo="updateTodo"
    />
    <TodoInput @addTodo="addTodo" />
  </div>
</template>
