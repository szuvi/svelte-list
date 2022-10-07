<script>
  import { onMount } from "svelte";
  import { getUsers } from "../api/getUsers";
  import Loader from "../Components/Loader.svelte";
  import TableHead from "../Components/TableHead.svelte";
  import UserRow from "../Components/UserRow.svelte";
  import { USER_TABLE_HEADERS } from "../consts";

  let users = [];

  onMount(async () => {
    users = await getUsers();
  });

  const toggleActive = (id) => {
    users = users.map((user) => {
      if (user.id === id) {
        return { ...user, active: !user.active };
      }
      return user;
    });
  };

  const deleteHandler = (id) => {
    users = users.filter((user) => user.id !== id);
  };
</script>

{#if users.length === 0}
  <Loader />
{:else}
  <table>
    <TableHead headers={USER_TABLE_HEADERS} />
    <tbody>
      {#each users as user (user.id)}
        <UserRow {user} onActivate={toggleActive} onDelete={deleteHandler} />
      {/each}
    </tbody>
  </table>
{/if}
