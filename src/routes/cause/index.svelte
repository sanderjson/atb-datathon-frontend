<script context="module">
  export function preload({ params, query }) {
    return this.fetch(`cause.json`)
      .then(r => r.json())
      .then(posts => {
        return { posts };
      });
  }
</script>

<script>
  import HomeCard from "../../components/HomeCard.svelte";
  import TopBar from "../../components/TopBar.svelte";
  export let posts;
</script>

<style>
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
  }
</style>

<svelte:head>
  <title>Local Initiatives</title>
</svelte:head>

<TopBar />

<ul>
  {#each posts as post, id}
    <li>
      <a rel="prefetch" href="cause/{post.slug}">
        <HomeCard {post} {id} />
      </a>
    </li>
  {/each}
</ul>
