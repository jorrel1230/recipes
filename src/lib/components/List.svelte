<script>
  let { items, ordered = false, renderItem } = $props()
</script>

<svelte:element this={ordered ? 'ol' : 'ul'} class="list" class:ordered role={ordered ? 'list' : undefined}>
  {#each items as item, index (item.id)}
    <li>
      {#if ordered}
        <span class="number" aria-hidden="true">{index + 1}</span>
      {/if}
      <div class="item-content">
        {#if renderItem}
          {@render renderItem(item)}
        {:else}
          {item.label}
        {/if}
      </div>
    </li>
  {/each}
</svelte:element>

<style>
  .list { margin: 0; padding-inline-start: 1.5rem; line-height: 1.7; }
  li + li { margin-block-start: 1.5rem; }
  .ordered { list-style: none; padding-inline-start: 0; }
  .ordered li { display: grid; grid-template-columns: subgrid; grid-column: 1 / -1; }
  .ordered { display: grid; grid-template-columns: max-content minmax(0, 1fr); column-gap: 1rem; }
  .number { font-size: 3rem; line-height: 1; font-variant-numeric: tabular-nums; }
</style>
