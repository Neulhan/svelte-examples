<script>
  import FontBox from "./font-box.svelte";
  let text = "그들의 장비와 기구는 모두 살아 있다.";
  let size = 32;

  const fontList = [
    "Noto Sans KR",
    "Nanum Myeongjo",
    "Nanum Gothic",
    "Gugi",
    "Jua",
    "Do Hyeon",
    "Black Han Sans",
    "Yeon Sung",
  ];
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
    width: 1300px;
    padding: 20px;
    box-sizing: border-box;
  }
  .top {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
  .top > input {
    box-sizing: border-box;
    padding: 12px;
    width: calc(50% - 10px);
    border-radius: 8px;
  }
  .center {
    margin-top: 100px;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
  }
</style>

<div class="page">
  <div class="container">
    <h1>국을 폰트</h1>
    <div class="top">
      <input
        placeholder="테스트 문자를 입력하세요"
        type="text"
        bind:value={text} />
      <input placeholder="폰트 사이즈" type="number" bind:value={size} />
    </div>
    <div class="center">
      {#each fontList as font}
        <FontBox {text} {font} {size} />
      {/each}
    </div>
  </div>
</div>
