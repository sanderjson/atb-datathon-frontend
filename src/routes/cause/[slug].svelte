<script context="module">
  export async function preload({ params, query }) {
    const res = await this.fetch(`cause/${params.slug}.json`);
    const data = await res.json();

    if (res.status === 200) {
      return { post: data };
    } else {
      this.error(res.status, data.message);
    }
  }
</script>

<script>
  export let post;

  console.log(post);
</script>

<style>

</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<div class="relative">
  <img src="./img/cause-{post.id}.jpg" alt="img for cause" />
  <div class="target absolute b-0">{post.target}</div>
</div>

<h1>{post.title}</h1>
<ul>
  {#each post.benefits as benefit}
    <li>{benefit}</li>
  {/each}
</ul>

{#each post.text as text}
  <p>{text}</p>
{/each}
