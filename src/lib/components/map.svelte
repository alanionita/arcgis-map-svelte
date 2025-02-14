<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import { browser } from '$app/environment';
	import WebMap from '@arcgis/core/WebMap';
	import MapView from '@arcgis/core/views/MapView';

	let mapView: MapView | undefined = $state();
	let mapContainer: HTMLDivElement | undefined = $state();
    let { lng = $bindable(), lat = $bindable() } = $props();

	onMount(() => {
		if (browser && mapContainer) {
			// Initialize the map only in the browser
			const webMap = new WebMap({
				basemap: 'streets-vector'
			});

			mapView = new MapView({
				container: mapContainer,
				map: webMap,
				center: [lng, lat], // Longitude, Latitude
				zoom: 12
			});

            mapView.watch('center', (center) => {
                const { latitude, longitude } = center;
                lat = latitude.toFixed(4);
                lng = longitude.toFixed(4);
            });

			return () => {
				if (mapView) {
					mapView.destroy();
				}
			};
		}
	});

	onDestroy(() => {
		if (mapView) {
			mapView.destroy();
		}
	});
</script>

{#if !browser}
    <p>Loading map...</p>
{:else}
    <div bind:this={mapContainer} class="arcgic-map"></div>
{/if}

<style>
	.arcgic-map {
		height: 100vh;
		width: 100vw;
	}
</style>
