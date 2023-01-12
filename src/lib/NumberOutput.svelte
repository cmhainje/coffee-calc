<script>
  import Number from "./Number.svelte";
  import { convert } from "./calc";

  export let name;
  export let numberLabel = name;
  export let value;

  let displayValue;
  let unit;

  function round(x) {
    if (x < 0) {
      throw new Error("no negative values allowed");
    } else if (x < 10) {
      return (Math.round(x * 100) / 100).toFixed(2);
    } else if (x < 100) {
      return (Math.round(x * 10) / 10).toFixed(1);
    } else {
      return Math.round(x);
    }
  }

  $: displayValue = round(value * convert["g"][unit]);
</script>

<Number {name} {numberLabel} disabled bind:value={displayValue} bind:unit />
