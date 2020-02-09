<script>
  export let segment;
  export let href;
  export let text;
  export let rel = "";
</script>

<style>
  .dash-text-active {
    color: var(--cl-white);
  }

  .dash-text {
    fill: var(--cl-grey);
  }

  :global(.dash-svg-active path) {
    fill: var(--cl-yellow);
  }
  :global(.dash-svg path) {
    fill: var(--cl-grey);
  }
</style>

<a
  {rel}
  {href}
  class="flex flex-col block mt-4 lg:mx-4 lg:inline-block lg:mt-0 {segment === href ? 'dash-svg-active' : 'dash-svg'}
  hover:text-white">
  <slot />
  <div class="{segment === href ? 'dash-text-active' : 'dash-text'} h1 text">
    {text}
  </div>
</a>
