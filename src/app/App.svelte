<script>
  import List from "./List.svelte";
  import TodoInput from "./TodoInput.svelte";
  import Filters from "./Filters.svelte";
  import { filters } from "./filters.json";

  let currentFilter = "all";

  let todos = [
    { id: 1, text: "Get some eggs", done: true },
    { id: 2, text: "Do some work", done: false }
  ];

  $: filteredTodos =
    currentFilter === "all"
      ? todos
      : currentFilter === "completed"
      ? todos.filter(todo => todo.done)
      : todos.filter(todo => !todo.done);

  $: remainingTodos = todos.filter(({ done }) => !done).length;

  function createTodo(id, text, done = false) {
    return { id, text, done };
  }

  function handleAdd(ev) {
    const data = new FormData(ev.target);
    const todo = data.get("todo");

    if (todo && todo.trim()) {
      todos = [...todos, createTodo(todos.length + 1, todo)];
    }
  }

  function toggleTodo(id) {
    todos = todos.map(todo => {
      if (todo.id === id) {
        todo.done = !todo.done;
      }
      return todo;
    });
  }

  function handleFilterChange(selection) {
    currentFilter = selection;
  }
</script>

<h1>Todo list</h1>
<p>Remaining Todos {remainingTodos}</p>
<TodoInput bind:handleAdd />
<List items={filteredTodos} bind:toggleTodo />
<Filters bind:handleFilterChange />
