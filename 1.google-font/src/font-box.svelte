<script>
  export let font;
  export let text;
  export let size;
</script>

<style>
  .font-box {
    width: 300px;
    background: #fff;
    border-radius: 8px;
    border: 1px solid #dadce0;
    box-shadow: 0px 0px 0px #fff, 0px 0px 0px #fff, 0px 0px 0px #fff;
    box-sizing: border-box;
    padding: 20px;
    margin-right: 20px;
    margin-bottom: 20px;
    transition: 0.18s ease all;
  }
  .font-box:hover {
    transform: scale(1.05);
  }
  :global(.font-box:nth-child(4n)) {
    margin-right: 0;
  }
</style>

<div
  class="font-box"
  style="font-family: '{font}', sans-serif; font-size: {size}px">
  {text}
</div>
