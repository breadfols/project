<script lang="ts">
	import RecentCard from './RecentCard.svelte';
	import { onMount } from 'svelte';
	import { register, type SwiperContainer } from 'swiper/element/bundle';
	import type { SwiperOptions } from 'swiper/types';
	import { api, type IFilm } from '$lib/database/films';
	const resents: Array<IFilm> = api.getResents();
	register();
	let swiperEl: SwiperContainer;

	const swiperParams: SwiperOptions = {
		slidesPerView: 1,
		spaceBetween: 20,
		loop: true,
		autoplay: {
			delay: 3000
		},
		injectStyles: [
			`
			.swiper {
				 overflow: visible;
			}
		`
		],
		breakpoints: {
			1440: {
				slidesPerView: 4
			},
			1024: {
				slidesPerView: 3
			},
			640: {
				slidesPerView: 2
			}
		}
	};

	onMount(() => {
		Object.assign(swiperEl, swiperParams);
		swiperEl.initialize();
	});
</script>

<div class="recents">
	<div class="container mx-auto">
		<h2 class="recents_title">Продолжить просмотр</h2>
		<!-- <div class="recents_items">
			<RecentCard />
			<RecentCard />
			<RecentCard />
			<RecentCard />
		</div> -->
		<swiper-container bind:this={swiperEl} init="false">
			{#each resents as film}
				<swiper-slide><RecentCard {film} /></swiper-slide>
			{/each}
		</swiper-container>
	</div>
</div>

<style>
	.recents {
		background: black;
		color: white;
		overflow: hidden;
		padding-bottom: 50px;
	}
	.recents_title {
		font-size: 20px;
		font-weight: 500;
		padding: 25px 0;
	}
</style>
