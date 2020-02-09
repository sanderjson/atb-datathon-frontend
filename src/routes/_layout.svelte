<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<Nav {segment}/>

<main class="lg:mt-20 container mx-auto p-4">
	<slot></slot>
</main>

<!-- <footer class="bg-black h-64 mt-8"> -->

<!-- </footer> -->