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
      {#each list as { id, text, complete }}
        <li class="item">
          {text}
          <div>
            <a
              on:click={toggleTask(id)}
              href="#"
            >
              {#if complete}
                Mark as incomplete
              {:else}
                Mark as complete
              {/if}
            </a>
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

<script lang="ts">
  import { onMount } from "svelte";
  import type {Item} from "./item.svelte";

  let list: Item[] = [];

  function getItems() {
    //request GET http://localhost:3000/

    const request = new XMLHttpRequest();
    request.open("GET", "http://localhost:3000/", true);
    request.send();

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 200) {
        list = JSON.parse(this.responseText);
      }
    }
  }

  function toggleTask(id: number) {
    //request PUT http://localhost:3000/{id}

    const item = list.find(item => item.id === id);
    if (item === undefined) {
      return;
    }
    item.complete = !item.complete;
    const request = new XMLHttpRequest();
    request.open("PUT", "http://localhost:3000/" + id.toString(), true);
    request.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
    request.send(JSON.stringify(item));

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 200) {
        getItems();
      }
    }
  }

  onMount(() => {
    console.log("Mounted")
    getItems();
  })
</script>