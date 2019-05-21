<script>
    import CustomInput from './CustomInput.svelte';
    import Toggle from './Toggle.svelte';

    let val = 'Stef';
    let selectedOption =1;

    $: console.log(val);
    $: console.log(selectedOption);

    function setValue(event) {
        val = event.target.value;
    }
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput type="text" bind:val={val} />

<!-- Avoid 2 way binding everywhere except forms and the like -->
<!-- To avoid introducing errors / complex behaviors, etc -->
<Toggle bind:chosenOption={selectedOption} />