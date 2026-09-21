<script lang="ts">
	import { format } from 'date-fns';
</script>

<svelte:head>
	<title>Dashboard | Workout log</title>
</svelte:head>
<section id="dashboard">
	<div class="mb-6 flex flex-wrap items-baseline justify-between gap-x-6 gap-y-2">
		<h1 class="font-display text-3xl font-bold tracking-tight sm:text-4xl">Dashboard</h1>
		<span class="text-sm font-semibold tabular-nums">
			{format(new Date(), 'EEEE, d LLLL')}
		</span>
	</div>
</section>
