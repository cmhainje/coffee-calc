<script>
  import NumberInput from "./lib/NumberInput.svelte";
  import { convert } from "./lib/calc";
  import NumberOutput from "./lib/NumberOutput.svelte";

  let volume = 16;
  let volumeUnit = "oz";
  let ratio = 17;
  let water_in_g;
  let coffee_in_g;

  let waterDensity = 0.997; // g / mL

  $: water_in_g = volume * convert[volumeUnit]["mL"] * waterDensity;
  $: coffee_in_g = water_in_g / ratio;
</script>

<main>
  <h1>coffee<br />calculator</h1>

  <NumberInput name="volume" bind:value={volume} bind:unit={volumeUnit} />
  <NumberInput name="ratio" disableUnits bind:value={ratio} />
  <hr />
  <NumberOutput name="water" bind:value={water_in_g} />
  <NumberOutput name="coffee" bind:value={coffee_in_g} />
</main>
