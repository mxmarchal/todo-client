<div>
  <h1>Edit</h1>

  You are editing {uuid}.
  <div>
    <input type="text" placeholder="Enter todo"
      bind:value={item}
    />
    <button
      on:click={edit}
    >
      Create
    </button>
  </div>
  <a href="/">Back</a>
</div>

<script>
  import { page } from '$app/stores';
  import { goto } from '$app/navigation';
  export const uuid = $page.params.uuid;

  //TODO: Get item from list
  let item = "test";

  export function edit() {
    console.log(item);
    if (item === '') {
      return;
    }
    //TODO: Edit item to list
    goto('/');
  }
</script>
