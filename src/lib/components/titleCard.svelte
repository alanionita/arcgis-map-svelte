<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	// Manchester: longitude, latitude,
	let { lng, lat }: { lng: number; lat: number } = $props();
</script>

<Card.Root>
	<Card.Header>
		<Card.Title>ArcGIS Map in SvelteKit</Card.Title>
	</Card.Header>
	<Card.Content>
		<p>Center latitude: {lat}</p>
		<p>Center longitude: {lng}</p>
	</Card.Content>
</Card.Root>
