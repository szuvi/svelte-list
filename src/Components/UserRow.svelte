<svelte:options immutable={true} />
<script>
  export let user;
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  const activateHandler = () => {
    dispatch("activate", user.id);
  };
  const deleteHandler = () => dispatch("delete", user.id);
</script>

<tr>
  {#each Object.values(user) as entry (entry)}
    <td>{entry.toString()}</td>
  {/each}
  <button type="button" on:click={activateHandler}>Activate</button>
  <button type="button" on:click={deleteHandler}>Delete</button>
</tr>
