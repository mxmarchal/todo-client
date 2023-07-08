<div>
  <h1>Create</h1>
  <div>
    <input type="text" placeholder="Enter todo"
      bind:value={text}
    />
    <button
      on:click={create}
    >
      Create
    </button>
  </div>
  <a href="/">Back</a>
</div>

<script>
  import { goto } from '$app/navigation';

  let text = '';

  export function create() {
    if (text === '') {
      return;
    }
    // request POST http://localhost:3000/
    const request = new XMLHttpRequest();
    request.open("POST", "http://localhost:3000/", true);
    request.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
    request.send(JSON.stringify({ text: text, complete: false }));

    request.onreadystatechange = function() {
      if (this.readyState === 4 && this.status === 200) {
        console.log(this.responseText);
        goto('/');
      }
    }
  }
</script>
