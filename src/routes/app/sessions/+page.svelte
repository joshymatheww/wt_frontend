<script lang="ts">
	import { goto } from '$app/navigation';
	import { getCurrentuser } from '$lib/apis/auth';
	import { authStore } from '$lib/stores/auth-store.svelte';
	import { onMount } from 'svelte';

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

<section id="sessions">
	<div class="mb-6 flex flex-wrap items-baseline justify-between gap-4">
		<div>
			<h1 class="font-display text-3xl font-bold tracking-tight sm:text-4xl">Sessions</h1>
			<p class="text-muted mt-1">— every day you've planned or trained.</p>
		</div>
		<a href="/app/sessions/new" class="rounded-md bg-ink px-4 py-2.5 text-sm font-medium text-panel"
			>New session</a
		>
	</div>
	<div class="mb-4 flex flex-wrap items-center gap-3 rounded-lg border border-line bg-panel p-4">
		<label class="relative min-w-[200px] flex-1">
			<svg
				viewBox="0 0 24 24"
				class="text-muted pointer-events-none absolute top-1/2 left-3 h-4 w-4 -translate-y-1/2"
				fill="none"
				stroke="currentColor"
				stroke-width="1.8"><circle cx="11" cy="11" r="6" /><path d="M20 20l-3.5-3.5" /></svg
			>
			<input
				type="search"
				placeholder="Search by title or notes"
				class="w-full rounded-md border border-line bg-page py-2 pr-3 pl-9 text-sm"
			/>
		</label>
		<select class="rounded-md border border-line bg-page px-3 py-2 text-sm">
			<option>All statuses</option><option>Planned</option><option>In progress</option><option
				>Completed</option
			><option>Skipped</option>
		</select>
		<select class="rounded-md border border-line bg-page px-3 py-2 text-sm">
			<option>All categories</option><option>Push</option><option>Pull</option><option>Legs</option
			><option>Core</option>
		</select>
	</div>
</section>
