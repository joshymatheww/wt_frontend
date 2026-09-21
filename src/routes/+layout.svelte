<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import { page } from '$app/state';
	import { authStore } from '$lib/stores/auth-store.svelte';
	import { goto } from '$app/navigation';

	let { children } = $props();

	$effect(() => {
		const currentRoute = page.url.pathname;
		const isPublicRoute = currentRoute === '/';

		if (isPublicRoute && authStore.token) {
			goto('/app');
		}
	});
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}
