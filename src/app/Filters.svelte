<script>
  import { filters } from "./filters.json";

  let selection = "all";
</script>

<style>
  .container {
    display: flex;
  }
  .item {
    margin-right: 10px;
  }
</style>

<h3>Filters</h3>

<div class="container">
  {#each Object.values(filters) as filter}
    <label class="item">
      <input
        type="radio"
        bind:group={selection}
        value={filter}
        on:change={() => $$props.handleFilterChange(selection)} />
      {filter.substring(0, 1).toUpperCase() + filter.substring(1)}
    </label>
  {/each}
</div>
