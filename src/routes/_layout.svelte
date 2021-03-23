<script>
	import { stores } from "@sapper/app";
	const { session, page } = stores();
	import Nav from '../components/Nav.svelte';

	page.subscribe((p) => {
		console.debug('[_layout.svelte, page.subscribe] called');
	})

	setTimeout(() => {
		session.update((s) => {
			console.debug('[_layout.svelte, session.update] called');
			return {...s}
		})
	}, 1000)

	export let segment;
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>