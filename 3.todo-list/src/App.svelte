<script>
  import { slide } from "svelte/transition";

  import Todo from "./Todo.svelte";
  import Done from "./Done.svelte";

  let todoList = [];
  let doneList = [];
  let text = "";

  let lastIndex = 0;

  const addTodo = () => {
    const id = lastIndex + 1;
    lastIndex = id;
    todoList.unshift({ text, id });
    todoList = todoList;
    text = "";
  };

  const moveItem = (id) => {
    const move = todoList.filter((item) => item.id === id);
    todoList = todoList.filter((item) => item.id != id);

    if (move.length > 0) {
      doneList.unshift(move[0]);
      doneList = doneList;
    }
  };
</script>

<style>
  :global(.page) {
    width: 100%;
    min-height: 800px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  :global(.container) {
    width: 620px;
    padding: 20px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
  }
  .wrapper {
    width: 620px;
    display: flex;
    justify-content: space-between;
  }
  section.list {
    width: 300px;
    border: 1px solid #eeeeee;
    padding: 8px;
    box-sizing: border-box;
  }
  :global(section.list > .card:last-child) {
    margin-bottom: 0;
  }
  .yet {
    color: #888;
    font-size: 14px;
  }
</style>

<div class="page">
  <div class="container">
    <h1>투두</h1>
    <section>
      <input type="text" bind:value={text} placeholder="TODO를 입력해주세요" />
      <button on:click={addTodo}>작성</button>
    </section>
    <div class="wrapper">
      <section class="todo-wrapper list">
        {#each todoList as todo}
          <Todo {moveItem} {todo} />
        {/each}
        {#if todoList.length === 0}
          <div class="yet" transition:slide>TODO 가 없습니다</div>
        {/if}
      </section>
      <section class="done-wrapper list">
        {#each doneList as done}
          <Done {done} />
        {/each}
        {#if doneList.length === 0}
          <div class="yet" transition:slide>DONE 이 없습니다</div>
        {/if}
      </section>
    </div>
  </div>
</div>
