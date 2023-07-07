<script>
  import { goto } from '$app/navigation';

  let item = '';

  export function create() {
    console.log(item);
    if (item === '') {
      return;
    }
    // TODO: Add item to list
    goto('/');

  }
</script>

<div>
  <h1>Create</h1>
  <div>
    <input type="text" placeholder="Enter todo"
      bind:value={item}
    />
    <button
      on:click={create}
    >
      Create
    </button>
  </div>
  <a href="/">Back</a>
</div>

