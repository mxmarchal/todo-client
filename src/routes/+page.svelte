<head>
  <title>
    {#if list.length === 0}
      No items
    {:else}
      {list.length} item(s)
    {/if}
    - Todo App
  </title>
</head>

<div>
  <h1>{list.length} items</h1>
  <ul id="list">
    {#if list.length === 0}
      <li>No items</li>
    {:else}
      {#each list as { id, value }}
        <li class="item">
          {value}
          <div>
            <a href="/create/{id}">Edit</a>
            <a href="/delete/{id}">Delete</a>
          </div>
        </li>
      {/each}
    {/if}
    <li class="item create">
      <a href="/create">Create</a>
    </li>
  </ul>
</div>

<script>
  import { onMount } from "svelte";

  export const list = [
    {
      id: "8888-8888-8888-8888",
      value: "Todo 1"
    },
    {
      id: "9999-9999-9999-9999",
      value: "Todo 2"
    }
  ]

  onMount(() => {
    console.log("Mounted")
    //TODO: Get list from API and set to list
  })
</script>