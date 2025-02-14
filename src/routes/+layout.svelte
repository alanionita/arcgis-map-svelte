<script lang="ts">
	import '../app.css';
	interface Props {
		children?: import('svelte').Snippet;
	}

	let { children }: Props = $props();
</script>

<main class="app">
	{@render children?.()}
</main>

<style>
	.app {
		display: flex;
		flex-direction: column;
	}
</style>