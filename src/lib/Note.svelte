<script>
	import { notes } from '$lib/store.js'

  export let id, content
  let show = true

  const deleteNote = () => {
    let filteredNotes = $notes.filter((note) => {
      if (note.id === id) {
        return false
      }
      else {
        return true
      }
    })
    $notes = filteredNotes
  }
</script>

{#if show}
  <section id="note">
    <p>{content}</p>
    <button class="delete" on:click={deleteNote}>Delete</button>
  </section>
{/if}

<style>
  * {
    font-family: Arial;
  }

  section {
    display: flex;
    flex-direction: column;
    width: 300px;
    outline: black 1px solid;
    border-radius: 10px;
    padding: 10px;
    margin-bottom: 10px
  }

  p {
    word-break: break-all;
    padding: 0;
    margin: 5px 0;
  }

  button {
    margin-top: 10px;
    max-width: 70px
  }
</style>
