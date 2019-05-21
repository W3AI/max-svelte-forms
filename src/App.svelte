<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";

  let val = "Stef";
  let price = 0;
  let selectedOption = 1;
  let agreed;
  let favCurrency = "Tims";
  let acceptedCurrencies = ["Tims","Smiles","Hughs"];

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);
  $: console.log(favCurrency);
  $: console.log(acceptedCurrencies);

  function setValue(event) {
    val = event.target.value;
  }
</script>

<h1>Accepted Currencies</h1>
<label>
  <input
    type="checkbox"
    name="accepted"
    value="Smiles"
    bind:group={acceptedCurrencies} />
  smiles :-)
</label>
<label>
  <input
    type="checkbox"
    name="accepted"
    value="Hughs"
    bind:group={acceptedCurrencies} />
  hughs
</label>
<label>
  <input
    type="checkbox"
    name="accepted"
    value="Shares"
    bind:group={acceptedCurrencies} />
  shares
</label>
<label>
  <input type="checkbox" name="accepted" value="USD" bind:group={acceptedCurrencies} />
  USD
</label>
<label>
  <input type="checkbox" name="accepted" value="CAD" bind:group={acceptedCurrencies} />
  CAD
</label>
<label>
  <input
    type="checkbox"
    name="accepted"
    value="Tims"
    bind:group={acceptedCurrencies} />
  coffee
</label>

<hr>
<h1>Inputs</h1>

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
  <input type="checkbox" bind:checked={agreed} />
  Agree to terms?
</label>

<hr />
<h1>Favorite Currency?</h1>
<label>
  <input type="radio" name="currency" value="USD" bind:group={favCurrency} />
  USD
</label>
<label>
  <input type="radio" name="currency" value="CAD" bind:group={favCurrency} />
  CAD
</label>
<label>
  <input type="radio" name="currency" value="Tims" bind:group={favCurrency} />
  coffee
</label>

<hr />



