<script lang="ts">
	import Nav from '../components/Nav.svelte';
</script>

<style>
	main {
		position: relative;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>

<Nav/>

<main>
	<slot></slot>
</main>
