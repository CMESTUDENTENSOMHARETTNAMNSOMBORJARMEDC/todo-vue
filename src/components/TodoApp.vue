<script>
let id = 0
export default {
  data() {
		return {
			newTodo: '',
  		todos: []
		}
  },
  methods: {
		createTodo() {
			this.todos.push({text: this.newTodo, id: id++, done: false})
			this.newTodo = ''
		},
		removeTodo(todo) {
			this.todos = this.todos.filter(e => e !== todo)
		},
  }
}
</script>

<template>
	<input v-model="newTodo" @keyup.enter="createTodo" />
	<button @click="createTodo">Add</button>
  <ul>
		<li v-for="todo in todos" :key="todo.id">
			<input type="checkbox" v-model="todo.done" />
  		<p :class="{ done: todo.done }"> {{ todo.text }} </p>
    	<button @click="removeTodo(todo)">X</button>
		</li>
  </ul>
</template>

<style>
ul {
  list-style: none;
	padding-inline-start: 0px;
}
p {
  display: inline;
	margin: 0.5em;
}
.done {
  text-decoration: line-through;
}
</style>

