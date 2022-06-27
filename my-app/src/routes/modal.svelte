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
		height: 100vh;
		position: absolute;
		top: 0px;
		right: 0px;
		bottom: 0px;
		left: 0px;
		background-color: rgba(192, 133, 133, 0.204);
	}

	.modal {
		margin: 0;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		max-width: 250px;
		height: 340px;
		text-align: center;
		background-color: rgba(24, 24, 24);
		border-radius: 10px;
	}
</style>
