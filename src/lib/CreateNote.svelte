<script>
	import { notes } from '$lib/store.js'

  let currentInput;

  function clearInput() {
    currentInput = undefined
  }

  function createNote() {
    if (currentInput) {
      $notes = [{id: Math.random().toString(36).substring(2, 7), title: "test", content: currentInput}, ...$notes]
    }
  }
  
  $: {
    console.log(currentInput)
  }
</script>

<textarea bind:value={currentInput}/>

<button class="create" on:click={createNote}>Create</button>
<button class="clear" on:click={clearInput}>Clear</button>

<style>
  * {
    font-family: Arial;
  }

  textarea {
    display: flex;
    flex-direction: column;
    width: 300px;
    border: none;
    outline: black 1px solid;
    border-radius: 10px;
    padding: 10px;
    resize: none;
    height: 50px;
  }

  button {
    margin-top: 5px;
    max-width: 70px
  }
</style>