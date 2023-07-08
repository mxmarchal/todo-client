<script>
  import { goto } from '$app/navigation';
  import { page } from '$app/stores';

  export const uuid = $page.params.uuid;

  export function deleteItem() {
    // request DELETE http://localhost:3000/{id}

    const request = new XMLHttpRequest();
    request.open("DELETE", "http://localhost:3000/" + uuid, true);
    request.send();

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 204) {
        console.log(this.responseText);
        goto('/');
      }
    }
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

