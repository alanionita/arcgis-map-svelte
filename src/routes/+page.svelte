<script lang="ts">
	import Map from '$lib/components/map.svelte';
	import TitleCard from '$lib/components/titleCard.svelte';
	import { browser } from '$app/environment';
	// Manchester: longitude, latitude,
	let lng: number = $state(-2.2446);
	let lat: number = $state(53.4839);
</script>

<TitleCard {lat} {lng} />

{#if !browser}
	<h2>Loading map...</h2>
{:else}
	<Map bind:lat bind:lng />
{/if}
