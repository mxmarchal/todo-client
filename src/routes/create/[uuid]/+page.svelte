<div>
  <h1>Edit</h1>

  You are editing {uuid}.
  <div>
    <input type="text" placeholder="Enter todo"
      bind:value={item.text}
    />
    <button
      on:click={edit}
    >
      Create
    </button>
  </div>
  <a href="/">Back</a>
</div>

<script lang="ts">
  import { page } from '$app/stores';
  import { goto } from '$app/navigation';
  import type {Item} from "../../item.svelte";
  import { onMount } from 'svelte';
  export const uuid = $page.params.uuid;


  let item: Item = {
    id: 0,
    text: '',
    complete: false
  };

  //TODO: Get item from list
  function getItem() {
    //request GET http://localhost:3000/{id}

    const request = new XMLHttpRequest();
    request.open("GET", "http://localhost:3000/" + uuid, true);
    request.send();

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 200) {
        item = JSON.parse(this.responseText);
      }
    }
  }

  export function edit() {
    if (item.text === '') {
      return;
    }
    // request PUT http://localhost:3000/{id}

    const request = new XMLHttpRequest();
    request.open("PUT", "http://localhost:3000/" + uuid, true);
    request.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
    request.send(JSON.stringify(item));

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 200) {
        console.log(this.responseText);
        goto('/');
      }
    }
  }

  onMount(() => {
    console.log("Mounted")
    getItem();
  })
</script>
