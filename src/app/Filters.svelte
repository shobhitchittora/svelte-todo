<script>
  import { filters } from "./filters.json";

  let selection = "all";

</script>

<h3>Filters</h3>

{#each Object.values(filters) as filter}
  <label>
    <input type="radio" bind:group={selection} value={filter} on:change={() => $$props.handleFilterChange(selection)}/>
    {filter.substring(0, 1).toUpperCase() + filter.substring(1)}
  </label>
{/each}
