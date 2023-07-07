<script>
  import { goto } from '$app/navigation';
  import { page } from '$app/stores';

  export const uuid = $page.params.uuid;

  export function deleteItem() {
    // TODO: Delete item to list
    console.log(`Deleting ${uuid}`)
    goto('/');

  }
</script>

<div>
  <h1>Delete</h1>
  <p>Do you want to delete {uuid}?</p>
  <div>
    <button
      on:click={deleteItem}
    >
      Delete
    </button>
    <a href="/">Back</a>
  </div>
</div>

