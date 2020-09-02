<script>
  let second = 0;
  let disabled = false;
  let loop;
  $: if (second >= 60) {
    second = 59;
  } else if (second < 0) {
    second = 0;
    disabled = false;
    clearInterval(loop);
  }

  const add = () => {
    second++;
  };
  const sub = () => {
    second--;
  };

  const start = () => {
    disabled = true;
    second--;
    loop = setInterval(() => {
      second--;
    }, 1000);
  };
</script>

<style>
  * {
    font-family: "Roboto", sans-serif;
  }
  :global(.page) {
    width: 100%;
    min-height: 800px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  :global(.container) {
    width: 1300px;
    padding: 20px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
  }
  section {
    width: 500px;
    height: 600px;
    margin: 100px auto;
  }
  .analog {
    overflow: hidden;
    border-radius: 100%;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px solid gold;
  }
  .hand {
    width: 1px;
    height: 100%;
    /* transition-duration: 1s; */
    transition-timing-function: linear;
    transition-delay: 0;
  }
  .visible {
    height: 50%;
    background-color: black;
  }
  .wrapper > div {
    display: flex;
    justify-content: center;
  }
  .up {
    font-size: 32px;
    margin: 1rem;
  }
</style>

<div class="page">
  <div class="container">
    <h1>타임얼</h1>
    <section>
      <div class="analog">
        <div class="hand" style="transform: rotate({second * 6}deg);">
          <div class="visible" />
        </div>
      </div>
      <div class="wrapper">
        <div class="up">{second}</div>
        <div class="down">
          <button {disabled} on:click={sub}>-</button>
          <button {disabled} on:click={start}>시작</button>
          <button {disabled} on:click={add}>+</button>
        </div>
      </div>
    </section>
  </div>
</div>
