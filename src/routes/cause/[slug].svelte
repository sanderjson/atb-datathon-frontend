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
  .target {
    background: var(--cl-green);
  }
</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<div class="relative">
  <img src="./img/cause-{post.id}.jpg" alt="img for cause" />
  <div class="target absolute bottom-0 p-4 text-white rounded-tr">
    Goal ${post.target}
  </div>
</div>

<header>
  <h1 class="text-2xl">{post.title}</h1>

  <button class="btn py-2 px-6 mx-auto">Donate $100.00</button>
</header>

<figure>
  <img
    src="https://via.placeholder.com/150"
    alt="charity icon"
    width="150"
    height="150" />
  <figcaption>{post.charity}</figcaption>
</figure>

<ul>
  {#each post.benefits as benefit}
    <li>{benefit}</li>
  {/each}
</ul>

{#each post.text as text}
  <p>{text}</p>
{/each}
