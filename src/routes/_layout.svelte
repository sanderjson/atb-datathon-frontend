<script>
  import Nav from "../components/Nav.svelte";
  import BottomBar from "../components/BottomBar.svelte";

  export let segment;
</script>

<main class="container mx-auto">
  <slot />
</main>

<footer class="bg-black h-32 mt-8" />
<BottomBar {segment} />
