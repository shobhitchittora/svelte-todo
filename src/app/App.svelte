<script>
  import List from "./List.svelte";
  import TodoInput from "./TodoInput.svelte";
  import Filters from "./Filters.svelte";
  import { filters } from "./filters.json";

  let items = [
    { id: 1, text: "Get some eggs", done: true },
    { id: 2, text: "Do some work", done: false }
  ];

  let filteredItems = items;

  function createTodo(id, text, done = false) {
    return { id, text, done };
  }

  function handleAdd(ev) {
    const data = new FormData(ev.target);
    const todo = data.get("todo");

    if (todo && todo.trim()) {
      items = [...items, createTodo(items.length + 1, todo)];
    }
  }

  function toggleTodo(id) {
    items = items.map(todo => {
      if (todo.id === id) {
        todo.done = !todo.done;
      }
      return todo;
    });
  }

  function handleFilterChange(selection) {
    switch (selection) {
      case filters.COMPLETED: {
        filteredItems = items.filter(({ done }) => done);
        break;
      }
      case filters.PENDING: {
        filteredItems = items.filter(({ done }) => !done);
        break;
      }
      default:
        filteredItems = items;
        break;
    }
  }
</script>

<h1>Todo list</h1>
<TodoInput bind:handleAdd />
<List items={filteredItems} bind:toggleTodo />
<Filters bind:handleFilterChange />
