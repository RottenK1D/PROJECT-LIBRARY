<script>
	import Modal from './modal.svelte';
	import Form from './add-book-form.svelte';

	let toggleModal = false;

	let library = [];

	function toggleForm() {
		toggleModal = !toggleModal;
	}

	function deleteBook(id) {
		library = library.filter((book) => book.id != id);
	}

	function addBook(e) {
		const book = e.detail;
		library = [book, ...library];
		toggleModal = false;
	}
</script>

<Modal {toggleModal} on:click={toggleForm}>
	<Form on:addBook={addBook} />
</Modal>

<main>
	<h1><a href="https://svelte.dev/">SVELTE</a> Book library demo</h1>
	<button on:click={toggleForm}>Add Book</button>
	{#each library as book (book.id)}
		<div class="book-card">
			<p>{book.author}</p>
			<p>{book.title}</p>
			<p>{book.pages}</p>
			<p>{book.read}</p>
			<button on:click={() => deleteBook(book.id)}>remove</button>
		</div>
	{/each}
</main>

<style>
	main {
		
	}

	h1 {
		
	}
</style>
