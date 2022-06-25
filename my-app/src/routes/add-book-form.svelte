<script>
	import { createEventDispatcher } from 'svelte';

	let dispatch = createEventDispatcher();

	let author;
	let title;
	let pages;
	let read = false;

	function doSubmit() {
		const book = {
			author,
			title,
			pages,
			read,
			id: Math.random()
		};

		dispatch('addBook', book);
	}
</script>

<form on:submit|preventDefault={doSubmit}>
	<h3>Add a new Book</h3>
	<input type="text" placeholder="author" bind:value={author} />
	<input type="text" placeholder="title" bind:value={title} />
	<input type="number" placeholder="pages" bind:value={pages} />
	<label>Did you read?<input type="checkbox" bind:checked={read} />Ya</label>
	<button>Add</button>
</form>

<style>
</style>
