<script>
  import { slide } from "svelte/transition";
  export let done = undefined;
</script>

<style>
  .card {
    padding: 24px;
    border: 1px solid #eeeeee;
    margin-bottom: 8px;
    border-radius: 2px;
    box-sizing: border-box;
    width: 100%;
  }
</style>

<div class="card" transition:slide>{done.text}</div>
