<section id="sessions">
	<div class="mb-6 flex flex-wrap items-baseline justify-between gap-4">
		<div>
			<h1 class="font-display text-3xl font-bold tracking-tight sm:text-4xl">Sessions</h1>
			<p class="text-muted mt-1"> — every day you've planned or trained.</p>
		</div>
		<a href="/app/sessions/new" class="rounded-md bg-ink px-4 py-2.5 text-sm font-medium text-panel"
			>New session</a
		>
	</div>
	<div class="mb-4 flex flex-wrap items-center gap-3 rounded-lg border border-line bg-panel p-4">
      <label class="relative flex-1 min-w-[200px]">
        <svg viewBox="0 0 24 24" class="pointer-events-none absolute left-3 top-1/2 h-4 w-4 -translate-y-1/2 text-muted" fill="none" stroke="currentColor" stroke-width="1.8"><circle cx="11" cy="11" r="6"/><path d="M20 20l-3.5-3.5"/></svg>
        <input type="search" placeholder="Search by title or notes" class="w-full rounded-md border border-line bg-page py-2 pl-9 pr-3 text-sm" />
      </label>
      <select class="rounded-md border border-line bg-page px-3 py-2 text-sm">
        <option>All statuses</option><option>Planned</option><option>In progress</option><option>Completed</option><option>Skipped</option>
      </select>
      <select class="rounded-md border border-line bg-page px-3 py-2 text-sm">
        <option>All categories</option><option>Push</option><option>Pull</option><option>Legs</option><option>Core</option>
      </select>
    </div>
</section>
