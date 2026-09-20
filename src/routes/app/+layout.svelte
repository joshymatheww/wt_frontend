<script lang="ts">
	import { goto } from '$app/navigation';
	import { getCurrentuser } from '$lib/apis/auth';
	import Header from '$lib/components/layout/Header.svelte';
	import Sidebar from '$lib/components/layout/Sidebar.svelte';
	import { authStore } from '$lib/stores/auth-store.svelte';
	import { onMount } from 'svelte';

	let { children } = $props();

	onMount(async () => {
		if (!authStore.token) {
			authStore.logout();
			goto('/');
		} else {
			try {
				authStore.isLoadingUser = true;
				const profile = await getCurrentuser(authStore.token);
				authStore.setUser(profile);
			} catch (error) {
				authStore.logout();
				goto('/');
			}
		}
	});
</script>

<Sidebar />

<div class="lg:pl-16">
	<Header />
	<main class="px-4 py-8 pb-24 sm:px-6 lg:px-8 lg:pb-8">
		{@render children()}
	</main>
</div>
