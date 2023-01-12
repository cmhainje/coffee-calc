<script>
  import Number from "./Number.svelte";

  export let name;
  export let numberLabel = name;

  export let value;
  export let unit = "oz";

  export let disableUnits = false;
</script>

<Number {name} {numberLabel} disableGrams {disableUnits} bind:value bind:unit />
