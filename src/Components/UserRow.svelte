<script>
  export let user;
  export let onActivate;
  export let onDelete;

  const activateHandler = () => onActivate(user.id);
  const deleteHandler = () => onDelete(user.id);
</script>

<tr>
  {#each Object.values(user) as entry (entry)}
    <td>{entry.toString()}</td>
  {/each}
  <button type="button" on:click={activateHandler}>Activate</button>
  <button type="button" on:click={deleteHandler}>Delete</button>
</tr>
