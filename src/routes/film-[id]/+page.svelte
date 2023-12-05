<script lang="ts">
	import FilmActors from '$lib/components/FilmPage/FilmActors.svelte';
	import FilmDescription from '$lib/components/FilmPage/FilmDiscription.svelte';
	import FilmFacts from '$lib/components/FilmPage/FilmFacts.svelte';
	import FilmInfo from '$lib/components/FilmPage/FilmInfo.svelte';
	import Navbar from '$lib/components/Header/Navbar.svelte';
	import type { IFilm } from '../../lib/database/films';
	export let data: { film: IFilm };
</script>

<div class="film-page">
	<Navbar />
	<FilmInfo film={data.film} />
	<FilmDescription description={data.film.description} />
	<FilmActors film={data.film} />
	<FilmFacts film={data.film} />
</div>

<style>
	.film-page {
		background-color: black;
		color: white;
	}
</style>