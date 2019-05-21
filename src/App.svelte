<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";
  import { isValidEmail } from './validation.js';

  let val = "Stef";
  let price = 0;
  let selectedOption = 1;
  let agreed;
  let favCurrency = "Tims";
  let acceptedCurrencies = ["JS","Smiles","Hughs", "CAD"];
  let singleFavCurrency = 'likes';
  let usernameInput;
  let someDiv;
  let customInput;
  let enteredEmail = '';
  let formIsValid = false;

    $: if (isValidEmail(enteredEmail)) {
        formIsValid = true;
    } else {
        formIsValid = false;
    }

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);
  $: console.log(favCurrency);
  $: console.log(acceptedCurrencies);
  $: console.log(singleFavCurrency);
  $: console.log(customInput);

  function setValue(event) {
    val = event.target.value;
  }

  function saveData() {
    //   console.log(document.querySelector('#username').value);    // Vanilla JS option
    console.log(usernameInput.value);
    console.dir(usernameInput);
    console.dir(someDiv);
    customInput.empty();
  }
</script>

<style>
    .invalid {
        border: 1px solid red;
     }
</style>

<h1>Svelte Form & Input Validation</h1>

<form on:submit|preventDefault>
<input type="email" bind:value="{enteredEmail}" class={isValidEmail(enteredEmail) ? '' : 'invalid'}>
<button type="submit" disabled={!formIsValid} >Email</button>
</form>

<hr>
<h1>Binding to Element References</h1>

<input type="text" id="username" bind:this={usernameInput}>
<button on:click="{saveData}">Save</button>

<p> bind:this= To be used for reading values from bound DOM elements </p>
<div bind:this={someDiv}>some text</div>

<hr>
<h1>Trading Options</h1>
<h3>List of options can be set dynamicall with #each}</h3> 
<h3>values can be objects too: e.g.: projects or services</h3>
<select bind:value={singleFavCurrency}>
    <option value="citations">Citations</option>
    <option value="likes">Likes</option>
    <option value="beers">Beers</option>
    <option value="bitcoins">Bitcoins</option>
</select>
<hr />
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
<label>
  <input
    type="checkbox"
    name="accepted"
    value="JS"
    bind:group={acceptedCurrencies} />
  scripts
</label>

<hr>
<h1>Inputs</h1>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput type="text" bind:val bind:this={customInput} />

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




