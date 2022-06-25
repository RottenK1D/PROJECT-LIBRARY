<script>
	export let toggleModal = false;
	export let isPromo = false;
</script>

{#if toggleModal}
	<div class="backdrop" class:promo={isPromo} on:click|self>
		<div class="modal">
			<slot />
		</div>
	</div>
{/if}

<style>
	.backdrop {
		width: 100%;
		height: 100%;
		position: static;
		background-color: rgba(0, 0, 0, 0.2);
	}

	.modal {
		position: relative;
		padding: 20px;
		max-width: 200px;
		border-radius: 10px;
		text-align: center;
		background-color: aliceblue;
		margin: 10% auto;
	}
</style>
