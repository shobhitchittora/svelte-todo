<script>
  let value;
  let handleAdd;
</script>

<style>
  .input {
    border: 1px solid grey;
  }
</style>

<form
  on:submit|preventDefault={ev => {
    value = '';
    $$props.handleAdd(ev);
  }}>
  <input bind:value type="text" name="todo" class="input" />
  <button type="submit">Add</button>
</form>
