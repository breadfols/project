<script lang="ts">
	import type { IFilm } from '$lib/database/films';

	export let film: IFilm;
	$: facts = film.facts.map((i) => i.value);
</script>

<div class="line" />
<div class="film-fact_wrapper">
	<div class="container mx-auto">
		<h2>Факты о фильме</h2>
		<ul class="film-facts">
			{#each facts as fact}
				<li class="film-facts_item">
					{@html fact}
				</li>
			{/each}
		</ul>
	</div>
</div>

<style>
	.line {
		border: 1px solid var(--light);
	}
	.film-facts {
		display: flex;
		flex-direction: column;
		gap: 35px;
		padding: 30px 0;
	}
	.film-facts_item {
		padding: 30px;
		border: 1px solid var(--light);
		border-radius: 15px;
		font-size: 18px;
	}
	.film-fact_wrapper {
		padding: 40px 0;
	}
</style>
