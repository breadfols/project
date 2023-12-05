<script lang="ts">
	import type { IRate } from "$lib/database/films";
	export let rate: IRate;
	export let img: string;
	let rateStatus: string = 'high';
	if (rate.kp < 7) {
		rateStatus = 'middle';
	}

	if (rate.kp < 4) {
		rateStatus = 'low';
	}
</script>

<div
	class="film-card"
	style:background={`url('${img}') no-repeat top`}
	style:background-size="cover"
>
	<div class="film-card_shadow">
		<span class="film-card_rate film-card_rate_{rateStatus}">{rate.kp.toFixed(1)}</span>
	</div>
</div>

<style>
	.film-card {
		height: 500px;
		border-radius: 10px;
	}
	.film-card_shadow {
		background: rgba(0, 0, 0, 0.8);
		padding: 5px 15px;
	}
	.film-card_rate {
		padding: 0 10px;
		border-radius: 3px;
	}
	.film-card_rate_high {
		background: var(--secondary);
	}
	.film-card_rate_middle {
		background: #777;
	}
	.film-card_rate_low {
		background: #8a0101;
	}
</style>
