<script>

</script>

<style>
  input[type="checkbox"] {
    padding-right: 10px;
    margin: 0 16px;
  }

  .done {
    text-decoration: line-through;
  }

  .remove {
    cursor: pointer;
    color: red;
    margin: 0 16px;
  }

  .item {
    list-style: none;
    display: flex;
    padding: 4px 0;
  }
</style>

<ul style="padding: 0;">
  {#each $$props.items as { id, text, done } (id)}
    <li class="item">
      <span class="remove" on:click={() => $$props.removeTodo(id)}>X</span>
      <input
        type="checkbox"
        checked={done}
        on:change={() => $$props.toggleTodo(id)} />
      <span class={done && 'done'}>{text}</span>
    </li>
  {/each}
</ul>
