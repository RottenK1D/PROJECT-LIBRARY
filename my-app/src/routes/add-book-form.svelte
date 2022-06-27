<script>
	import { createEventDispatcher } from 'svelte';
	import { readable } from 'svelte/store';

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
			read: read == false ? '👎' : '👍',
			id: Math.random()
		};

		dispatch('addBook', book);
	}
</script>

<form on:submit|preventDefault={doSubmit}>
	<input type="text" placeholder="author" bind:value={author} required />
	<input type="text" placeholder="title" bind:value={title} required />
	<input type="number" placeholder="pages" bind:value={pages} required />
	<label>Did you like it?<input type="checkbox" bind:checked={read} /></label>
	<button>submit</button>
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		margin: 40px 20px;
	}

	input,
	label {
		font-weight: bold;
		margin-bottom: 10px;
		font-size: 1.2rem;
		padding: 5px;
		height: 30px;
		border-radius: 5px;
		color: #ff3e00;
	}

	input[type='checkbox'] {
		width: 1.15em;
		height: 1.15em;
		transform: translateY(-0.075em);
	}

	button {
		cursor: pointer;
		padding: 10px;
		border: none;
		background: #ff3e00;
		font-size: 1.5rem;
		font-weight: bold;
		border-radius: 5px;
	}
</style>
