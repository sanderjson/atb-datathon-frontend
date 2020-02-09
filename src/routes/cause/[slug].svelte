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
  import Benefits from "../../components/Benefits.svelte";
  export let post;

  // import { buttonAmount } from "../../stores.js";
  import { usrAmount } from "../../stores.js";


  let donateValue;

  const unsubscribe = usr.subscribe(value => {
    donateValue = value;
  });

  // console.log(post);
</script>

<style>
  img.hero {
    display: block;
    min-height: 320px;
    object-fit: cover;
  }

  .target {
    background: var(--cl-green);
  }

  .header {
    display: grid;
    row-gap: 2em;
    align-items: center;
    grid-template-areas:
      "title title"
      "img btn"
      "caption hashtag";
  }

  .header h1 {
    grid-area: title;
  }
  .header .img {
    height: 120px;
    width: 120px;
    display: grid;
    place-items: center;
    border: 2px solid var(--cl-grey);
  }
  .header .img img {
    max-width: 80px;
  }
  .header .caption {
    grid-area: caption;
    align-self: flex-start;
    color: var(--cl-grey-dark);
  }

  .header .button {
    align-self: center;
    grid-area: btn;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
  }

  .header .hashtag {
    grid-area: hashtag;
    align-self: flex-start;
    color: var(--cl-grey-dark);
    justify-self: center;
  }

  button {
    min-width: 150px;
  }
</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<div class="relative">
  <img class="hero" src="./img/{post.hero}" alt="img for cause" />
  <div class="target absolute bottom-0 p-4 text-white rounded-tr">
    Goal ${post.target}
  </div>
</div>

<header class="header my-8 px-2 mx-auto leading-normal">
  <h1 class="text-xl sm:text-2xl ml-2">{post.title}</h1>
  <div class="img rounded ml-2">
    <img src="./img/{post.logo}" alt="charity icon" />
  </div>
  <div class="caption ml-2">
    with
    <span class="hightlight">
      {post.charity}
      <span />
    </span>
  </div>
  <div class="button">
    <button
      class="my-4 btn btn-pri text-white py-2 px-8 mx-auto rounded text-lg
      sm:text-2xl shadow-xl hover:shadow-2xl trans-shadow ">
      Donate ${donateValue}
    </button>
    <button
      class="my-4 btn btn-sec py-2 px-6 mx-auto rounded text-lg sm:text-2xl
      shadow-xl hover:shadow-2xl trans-shadow ">
      Donate Other
    </button>
  </div>
  <div class="hashtag">{post.hashtag}</div>
</header>

<hr class="hr mx-4" />

<section class="my-8 px-2 mx-auto">
  <h2 class="my-2 ml-2">
    Support
    <span class="hightlight">{post.hashtag}</span>
  </h2>
  <Benefits benefits={post.benefits} />

</section>
<hr class="hr mx-4" />

<section class="my-8 px-2 mx-auto">
  <h2 class="my-2 ml-2">
    About
    <span class="hightlight">{post.hashtag}</span>
  </h2>
  {#each post.text as text}
    <p class="ml-2 my-2">{text}</p>
  {/each}

</section>

<hr class="hr mx-4" />
<section class="my-8 px-2 mx-auto">
  <h2 class="my-2">
    About
    <span class="hightlight">{post.charity}</span>
  </h2>
  <p class="ml-2 my-2">
    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Repudiandae
    voluptatum deleniti unde repellendus itaque?
  </p>
  <p class="ml-2 my-2">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Architecto impedit
    nihil explicabo tenetur quas? Illum voluptas dolorem velit deserunt
    provident.
  </p>

</section>
