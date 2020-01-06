<script>
  import List from "./List.svelte";
  import TodoInput from "./TodoInput.svelte";

  let items = [
    { id: 1, text: "Get some eggs", done: true },
    { id: 2, text: "Do some work", done: false }
  ];

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
</script>

<h1>Todo list</h1>
<TodoInput bind:handleAdd />
<List bind:items />
