<script lang="ts">
	import "../app.css";
	import Footer from "./footer/Footer.svelte";
	import Header from "./header/Header.svelte";

	let { children } = $props();
</script>

<div class="w-screen h-screen flex justify-center">
	<div class="flex flex-col bg-white w-[min(100%,_1400px)] h-full">
		<div class="p-2">
			<Header />
		</div>

		<main class="grow px-2">
			{@render children()}
		</main>

		<Footer />
	</div>
</div>
