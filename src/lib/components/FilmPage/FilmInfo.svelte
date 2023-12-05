<script lang="ts">
	import type { IFilm } from '$lib/database/films';
	export let film: IFilm;
	$: genres = film.genres.map((i) => i.name);
	$: countries = film.countries.map((i) => i.name);
	$: directors = film.persons.filter((i) => i.enProfession === 'director').map((i) => i.name);
</script>

<div class="line">
	<div class="container mx-auto">
		<div class="film-info">
			<div class="film-info_detail">
				<h1>{film.name}</h1>
				<div>
					<div>Год: {film.year}</div>
					<div>Жанр: {genres.join(', ')}</div>
					<div>Страна: {countries.join(', ')}</div>
					<div>{directors.length > 1 ? 'Режиссеры:' : 'Режиссер:'} {directors.join(', ')}</div>
				</div>
				<div class="film-info_description">
					{film.shortDescription}
				</div>
				<div class="film-info_rate">
					<div class="flex items-center gap-3">
						<img src="/icon/rate1.svg" alt="rate" />{film.rating.kp.toFixed(1)}
					</div>
					<div class="flex items-center gap-3">
						<img src="/icon/rate2.svg" alt="rate" />{film.rating.imdb.toFixed(1)}
					</div>
				</div>
			</div>
			<div class="film-info_img film_img">
					<img  src={film.backdrop.url} alt={film.name} />
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	.line {
		border-top: 1px solid var(--light);
	}
	.film-info {
		display: grid;
		grid-template-columns: 40% 60%;
		padding: 40px 0;
		@media (max-width: theme('screens.desktop')) {
			display: flex;
			flex-direction: column-reverse;
			gap: 50px;
			padding: 30px 0;
		}
	}
	.film_img {
		border-radius: 6%;
	}
	.film-info_img {
		width: 100%;
		height: 100%;
		overflow: hidden;
	}
	.film-info_description {
		padding: 42px 0;
	}
	.film-info_rate {
		display: flex;
		align-items: center;
		gap: 32px;
	}
	.film-info_detail {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		font-size: 18px;
		padding-right: 50px;
		@media (max-width: theme('screens.desktop')) {
			gap: 30px;
		}
	}
</style>
