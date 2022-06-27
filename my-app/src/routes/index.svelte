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

<main>
	<h1><a href="https://svelte.dev/">SVELTE</a> bookCase</h1>
	<div class="add">
		<button on:click={toggleForm}>Add Book</button>
		<Modal {toggleModal} on:click={toggleForm}>
			<Form on:addBook={addBook} />
		</Modal>
	</div>
	<div class="bookcase">
		{#each library as book (book.id)}
			<div class="book-card">
				<p>{book.author}</p>
				<p>{book.title}</p>
				<p>{book.pages}</p>
				<p>{book.read}</p>
				<button on:click={() => deleteBook(book.id)}>remove</button>
			</div>
		{/each}
	</div>
</main>

<style>
	h1 {
		margin: 0;
		padding: 20px;
		box-sizing: border-box;
		font-size: 3.5rem;
		border-bottom: 2px solid #ff3e00;
	}

	a {
		outline: none;
		text-decoration: none;
		color: #ff3e00;
		transition: 0.2s;
	}

	a:hover,
	a:focus {
		color: #40b3ff;
	}

	.add {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.add button {
		cursor: pointer;
		margin-top: 20px;
		padding: 15px;
		border: none;
		background: rgba(243, 166, 166, 0.248);
		font-size: 2rem;
		font-weight: bold;
		border-radius: 10px;
		transition: 0.3s;
	}

	.add button:hover,
	button:focus {
		background: #ff3e00;
	}

	.bookcase {
		display: flex;
		margin: 100px;
	}

	.bookcase p {
		font-size: 1.5rem;
	}

	.book-card {
		background-color: #ff3e00;
		margin: 20px;
		padding: 20px;
		width: 200px;
		text-align: center;
		font-size: 2rem;
		font-weight: bold;
		border-radius: 10px;
	}

	.book-card > button {
		color: #ff3e00;
		cursor: pointer;
		padding: 10px;
		border: none;
		background: black;
		font-size: 1.5rem;
		font-weight: bold;
		border-radius: 5px;
		transition: 0.3s;
	}

	.book-card > button:hover {
		scale: 0.9;
	}
</style>
