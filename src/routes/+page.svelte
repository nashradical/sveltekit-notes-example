<script>
	import Note from '$lib/Note.svelte'
	import CreateNote from '$lib/CreateNote.svelte'
	import { notes } from '$lib/store.js'

	if (!localStorage.getItem("notesApp")) {
		localStorage.setItem("notesApp", JSON.stringify([{id: 1,content: 'Here is an example note'},{id: 2,content: 'Clean the dishes, do laundry'}]))
	}

	$notes = JSON.parse(localStorage.getItem("notesApp"))

	$: {
		localStorage.setItem("notesApp", JSON.stringify($notes))
	}
</script>

<h1>Notes App</h1>
<CreateNote/>
<hr>
{#each $notes as note, i}
	<Note {...note}/>
{/each}

<style>
  * {
    font-family: Arial;
		margin: 0;
		padding: 0;
  }

	hr {
		margin: 20px 0;
	}
</style>