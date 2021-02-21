<script lang="ts">
	export let labelText: string
	export let placeholder: string
	export let value: string
	export let id: string
    export let type: string
    export let onFocusOut: any
    export let min: string
    export let max: string
    export let errorMessage: string
	import { onMount } from 'svelte';

	onMount(() => {
        document.getElementById(id).addEventListener('focusout', onFocusOut)
	});

    function showError(): string {
        return errorMessage != undefined ? 'error' : 'error-label'
    }

    function hasError(): string {
        return errorMessage != undefined ? 'error-input' : ''
    }
</script>

<style>
    .input {
        display: grid;
        grid-gap: 0.25rem;
        width: 100%;
    }

    .input > span {
        font-size: 12px;
        font-weight: bolder;
    }

    .input > input {
        border: 1px solid lightgrey;
        border-radius: 8px;
        outline: none;
        padding: 0.5rem;
    }

    .error {
        color: red;
    }

    .error-label {
        display: none;
    }

    input.error-input {
        border: 1px solid red;
    }

</style>

<div class="input">
    <span>{labelText}</span>
    <input id={id} class={hasError()} type={type} value={value} placeholder={placeholder} min={min} max={max}>
    <p class={showError()}>{errorMessage}</p>
</div>
