<script>
  export let name;
  export let numberLabel;
  export let value;
  export let unit;

  export let disabled = false;
  export let disableUnits = false;
  export let disableGrams = false;
</script>

<div class="number">
  <div class="label-container"><label for={name}>{numberLabel}</label></div>
  <input type="number" {name} {disabled} inputmode="decimal" bind:value />

  {#if !disableUnits}
    <select class="unit-picker" bind:value={unit}>
      {#if !disableGrams}
        <option value="g">g</option>
      {/if}
      <option value="mL">mL</option>
      <option value="oz">fl oz</option>
    </select>
  {:else}
    <div class="unit-picker" />
  {/if}
</div>

<style>
  .number {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;

    padding-top: 4px;
    padding-bottom: 4px;
  }

  .label-container {
    display: inline-block;
    min-width: 80px;
    text-align: right;
    margin-right: 20px;
  }

  .unit-picker {
    margin-left: 10px;
    display: inline-block;
    width: 56px;
    min-height: 1px;
  }

  input[type="number"] {
    padding: 2px 10px;
    font-size: 60px;
    width: 4ch;
    text-align: center;
    background-color: #e8e8e8;
    border: 1px solid black;
    border-radius: 4px;
  }

  input[type="number"]::-webkit-outer-spin-button,
  input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  input[type="number"]:disabled {
    color: black;
    border: none;
  }
</style>
