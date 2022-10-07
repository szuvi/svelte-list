<script>
  export let headers = [];
</script>

<thead>
  <tr>
    {#each headers as header (header)}
      <th>{header}</th>
    {/each}
  </tr>
</thead>
