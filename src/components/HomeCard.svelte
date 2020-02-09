<script>
  export let post;
  export let id;
</script>

<style>
  .target {
    background: var(--cl-green);
  }
  .card {
    max-width: 90%;
    border: 1px solid var(--cl-grey);
  }
</style>

<article
  class="card my-8 mx-auto class rounded shadow-xl hover:shadow-2xl trans-shadow">
  <div class="relative">
    <img class="hero" src="./img/{post.hero}" alt="img for cause" />
    <div class="target absolute bottom-0 p-4 text-white rounded-tr">
      Goal ${post.target}
    </div>
  </div>
  <div class="content my-6">
    <h1 class="text-xl sm:text-2xl ml-2">{post.title}</h1>
    <div class="caption ml-2">
      with
      <span class="hightlight">
        {post.charity}
        <span />
      </span>
    </div>
  </div>
</article>
