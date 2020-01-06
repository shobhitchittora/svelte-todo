<script>

</script>

<style>
  input[type="checkbox"] {
    padding-right: 10px;
  }
</style>

<ul>
  {#each $$props.items as { id, text, done } (id)}
    <li style="list-style: none;">
      <input type="checkbox" checked={done} />
      {text}
    </li>
  {/each}
</ul>
