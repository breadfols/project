<script>
	import Search from '$lib/components/Common/Search.svelte';
	import Pagination from '../Common/Pagination.svelte';
	import FilmCard from './FilmCard.svelte';
	import { api } from '$lib/database/films';
	import {} from '$app/stores';
	import { page } from '$app/stores';
	let searchQuery = '';
	$: filmsData = api.getFilms(currentPage, searchQuery);
	$: currentPage = Number($page.url.searchParams.get('page')) || 1;
</script>

<div class="films">
	<div class="container mx-auto">
		<div class="flex items-center justify-between mb-[30px] relative">
			<!-- svelte-ignore a11y-missing-content -->
			<a id="title" class="anchor"/>
			<h2>Все фильмы</h2>
			<Search on:input={(e) => (searchQuery = e.detail)} />
		</div>
		<div class="films_grid">
			{#each filmsData.items as film}
			{#key film.id}
				<a href="/film-{film.id}">
					<FilmCard rate={film.rating} img={film.poster.previewUrl} />
				</a>
				{/key}
			{/each}
		</div>
		<div class="flex justify-center tablet:justify-end">
			<Pagination {currentPage} maxPage={filmsData.maxPage} />
		</div>
	</div>
</div>

<style lang="scss">
	.anchor{
		position: absolute;
		top:-20px;
	}
	.films {
		background: black;
		color: white;
		padding: 50px 0;
		border-top: 1px solid var(--light);
	}
	.films_grid {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 30px;
		margin-bottom: 30px;
		@media (max-width: theme('screens.desktop')) {
			grid-template-columns: repeat(3, 1fr);
		}
		@media (max-width: theme('screens.laptop')) {
			grid-template-columns: repeat(2, 1fr);
		}
		@media (max-width: theme('screens.tablet')) {
			grid-template-columns: 1fr;
		}
	}
</style>
