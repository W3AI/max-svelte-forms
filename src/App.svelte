<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";

  let val = "Stef";
  let price = 0;
  let selectedOption = 1;
  let agreed;

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);

  function setValue(event) {
    val = event.target.value;
  }
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput type="text" bind:val />

<!-- Avoid 2 way binding everywhere except forms and the like -->
<!-- To avoid introducing errors / complex behaviors, etc -->
<Toggle bind:chosenOption={selectedOption} />

<!-- <input
  type="number"
  value={price}
  on:input={event => console.log(1 + event.target.value)} /> -->

<input type="number" bind:value={price} />

<label>
  <input type="checkbox" bind:checked={agreed}/>
  Agree to terms?
</label>
