<script>
  let userInput = "";
  let handleAdd;
</script>

<style>
  .input {
    border: 1px solid grey;
  }
</style>

<form
  on:submit|preventDefault={ev => {
    userInput = '';
    $$props.handleAdd(ev);
  }}>
  <input bind:value={userInput} type="text" name="todo" class="input" />
  <button type="submit">Add</button>
</form>
