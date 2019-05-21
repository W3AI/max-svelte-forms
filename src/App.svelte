<script>
    import CustomInput from './CustomInput.svelte';
    import Toggle from './Toggle.svelte';

    let val = 'Stef';

    $: console.log(val);

    function setValue(event) {
        val = event.target.value;
    }
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput type="text" bind:val={val} />

<Toggle />