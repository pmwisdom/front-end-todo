<script>
  import Todo from "./Todo.svelte";

  let todos = ["Hello", "World"];
  $: inputText = "";

  function handleInputChange(evt) {
    console.log("Changed");
    inputText = evt.currentTarget.value;
  }

  function handleAddTodo() {
    console.log("input text", inputText);
    todos = [...todos, inputText];
    inputText = "";
  }

  function handleInputKeyDown(evt) {
    // Enter
    if (evt.keyCode === 13) {
      handleAddTodo();
    }
  }

  function handleRemoveTodo(index) {
    todos = todos.filter((v, i) => i !== index);
  }
</script>

<div>
  <input
    on:change={handleInputChange}
    on:keyup={handleInputKeyDown}
    value={inputText}
  />
  <button on:click={handleAddTodo}> Add </button>

  {#each todos as todo, i}
    <Todo {todo} index={i} onRemoveTodo={handleRemoveTodo} />
  {/each}
</div>

<style>
  button {
    cursor: pointer;
  }
</style>
