<script>
	
	import Nav from './components/Nav.svelte'
	import Typer from "./components/Typewriter.svelte";
		import LeftPanel from "./components/LeftPanel.svelte";
	let v ;
</script>

<main>
<!-- <Nav /> -->
<Typer bind:v={v}/>
<LeftPanel bind:v={v} />



</main>

<style>
	main {
		color: white;
		padding: 1em;
	}
</style>