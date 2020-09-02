<script>
  import { slide } from "svelte/transition";
  export let todo = undefined;
  export let moveItem;
  let checked;
</script>

<style>
  .card {
    padding: 24px;
    border: 1px solid #eeeeee;
    margin-bottom: 8px;
    border-radius: 2px;
    box-sizing: border-box;
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .icon {
    cursor: pointer;
  }
</style>

<div class="card" transition:slide={{ duration: 200 }}>
  <div class="text">{todo.text}</div>
  <div class="icon" on:click={moveItem(todo.id)}>▶️</div>
</div>
