<script>
  import { onMount } from "svelte";
  import * as d3 from "d3";
  var data = [30, 86, 168, 281, 303, 365];

  let el;

  onMount(() => {
    d3.select(el)
      .selectAll("div")
      .data(data)
      .enter()
      .append("div")
      .style("width", function(d) {
        return d + "px";
      })
      .text(function(d) {
        return d;
      });
  });
</script>

<style>
  .chart :global(div) {
    font: 10px sans-serif;
    background-color: steelblue;
    text-align: right;
    padding: 3px;
    margin: 1px;
    color: white;
  }
</style>


<div bind:this={el} class="chart" />

<!-- <script context="module">
  export async function preload() {
    const res = await this.fetch(
      `https://dev.to/api/articles?username=jpblancodb`
    //   https://api.leapos.ca/obp/v4.0.0/banks/dc6c74fe14787f411e8c7a6c3991fe8/accounts/9043177494179-b6eed5d7-bb0/owner/transactions

    );
    return { articles: await res.json() };
  }
</script>  export let articles;
  console.log(articles)
<script>

{articles}
<h1>Data Charts Will Go Here</h1> -->
