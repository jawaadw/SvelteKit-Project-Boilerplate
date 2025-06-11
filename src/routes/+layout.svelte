<script lang="ts">
	import "../app.css";
	import Footer from "./footer/Footer.svelte";
	import Header from "./header/Header.svelte";

	let { children } = $props();
</script>

<div id="display-body">
	<Header />

	{@render children()}

	<Footer data={{}} />
</div>

<style>
	#display-body {
		display: flex;
		flex-direction: column;
		background-color: white;
		width: min(100%, 1400px);
		height: 100vh;
	}

	#main-content {
		flex-grow: 1;
	}
</style>
