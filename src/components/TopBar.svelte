<script>
  import { onMount } from "svelte";

  let crd = {};
  let options = {
    enableHighAccuracy: true,
    timeout: 5000,
    maximumAge: 0
  };

  onMount(() => {
    function success(pos) {
      crd = pos.coords;

      //   console.log("Your current position is:");
      //   console.log(`Latitude : ${crd.latitude}`);
      //   console.log(`Longitude: ${crd.longitude}`);
      //   console.log(`More or less ${crd.accuracy} meters.`);
    }
    function error(err) {
      console.warn(`ERROR(${err.code}): ${err.message}`);
    }
    navigator.geolocation.getCurrentPosition(success, error, options);
  });
</script>

<style>
  .top-bar {
    width: 100%;
    background: var(--cl-green);
    color: var(--cl-white);
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
  }

  .top-bar .location {
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    color: var(--cl-grey);
    text-transform: uppercase;
    line-height: 1.2;
  }

  .top-bar .location span {
    color: var(--cl-white);
  }
</style>

<section class="top-bar text-xl py-2">
  <div class="h1">Top Causes in Your Area</div>
  {#if crd}
    <div class="location text-sm">
      <div class="my-0">
        latitude:
        <span>{JSON.stringify(crd.latitude, 0, 2)}</span>
      </div>
      <div class="my-0">
        longitude:
        <span>{JSON.stringify(crd.longitude, 0, 2)}</span>
      </div>
    </div>
  {/if}
</section>
