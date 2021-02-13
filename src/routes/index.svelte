<script>
	import Countdown from '../components/Countdown.svelte';
import TextInput from '../components/TextInput.svelte';
</script>

<style>
	.countdown {
		text-align: center;
	}
</style>

<svelte:head>
	<title>Countdown timer</title>
</svelte:head>

<div class="countdown">
	<Countdown/>
</div>
