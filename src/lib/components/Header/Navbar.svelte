<script>
	import DcButton from '../Common/DCButton.svelte';
</script>

<div class="navbar">
	<div class="container mx-auto flex items-center justify-between">
		<a href="/" class="navbar_img">KINFLIX</a>
		<DcButton>Войти</DcButton>
	</div>
</div>

<style>
	.navbar_img {
		color: var(--primary, #b6070a);
		text-align: center;
		font-family: Inter;
		font-size: 28px;
		font-style: normal;
		font-weight: 700;
		line-height: normal;
	}
	.navbar {
		background: rgba(0, 0, 0, 0.5);
		padding: 10px 0;
	}
</style>
