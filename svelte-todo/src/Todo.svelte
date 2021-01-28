<script>
  export let todo;
  export let index;
  export let onRemoveTodo;

  let hovering = false;

  function enter() {
    hovering = true;
  }

  function leave() {
    hovering = false;
  }
</script>

<div class="container" on:mouseenter={enter} on:mouseleave={leave}>
  <span>{todo}</span>

  {#if hovering}
    <span class="delete" on:click={(e) => onRemoveTodo(index)}>x</span>
  {/if}
</div>

<style>
  .container {
    border: 1px lightgray solid;
    padding: 10px;
    margin: 8px;
    border-radius: 6px;
    position: relative;
  }

  .delete {
    position: absolute;

    right: 6px;
    top: 4px;
    bottom: 0;
    color: red;
    font-size: 22px;
    cursor: pointer;
  }
</style>
