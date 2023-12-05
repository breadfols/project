<script lang="ts">
	export let description:string;
</script>

<div class="film-discription">
	<div class="container mx-auto">
		<h2 class="film-discription_title">Описание</h2>
		<p>
			{description}
		</p>
	</div>
</div>

<style>
	.film-discription {
		border-top: 1px solid var(--light);
		padding: 30px 0;
		font-size: 18px;
		padding-top: 35px;
		padding-bottom: 30px;
	}
	.film-discription_title {
		font-size: 25px;
		font-weight: 700;
	}
</style>
