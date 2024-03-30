<script>
  import { fade } from "svelte/transition";

  let books = ["ドグラ・マグラ", "黒死館殺人事件", "虚無への供物"];
  let newBook = "";

  function addBook(evt) {
    if (evt.key === "Enter") {
      books = [...books, newBook];
      newBook = "";
    }
  }
</script>

<label>
  <h4>Add Book</h4>
  <input type="text" bind:value={newBook} on:keydown={addBook} />
</label>
<h4>My Books</h4>
<ul>
  {#each books as book}
    <li transition:fade>{book}</li>
  {/each}
</ul>

<style>
  input {
    padding: 5px 10px;
  }
  li {
    list-style: none;
  }
  ul {
    padding: 5px 0;
  }
</style>
