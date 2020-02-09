<script>
  export let title;
  export let id;

  console.log(id);
</script>

<style>
  .card {
    transition: box-shadow 0.3 ease;
  }

  .card .overlay {
    background: var(--cl-pri);
    /* opacity: 0.382; */
    opacity: 0.191;
    mix-blend-mode: screen;
    /* mix-blend-mode: multiply; */

  }

  .card header {
    margin-top: 5%;
  }
</style>

<div
  class="card relative mt-8 rounded shadow-xl hover:shadow-2xl trans-shadow ">
  <img
    class="object-cover"
    style="max-height: 33vh; width: 100%"
    src="./img/cause-{id + 1}.jpg"
    alt="" />

  <div style="height: 100px" />

  <div class="overlay absolute inset-0 h-full w-full" />
  <div class="absolute inset-0 h-full w-full">
    <header class="text-center">
      <h1 class="text-lg lg:text-2xl">{title}</h1>
    </header>
  </div>

</div>
