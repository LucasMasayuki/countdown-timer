<script lang="ts">
	export let defaultText = ''
	export let placeholder = ''
	export let labelText = 'test'
</script>

<style>
    .text-input {
        display: grid;
        grid-gap: 0.25rem;
        width: min-content;
    }

    .text-input > span {
        font-size: 12px;
        font-weight: bolder;
    }

    .text-input > input {
        border: 1px solid lightgrey;
        border-radius: 8px;
        outline: none;
        padding: 0.5rem;
    }

</style>

<div class="text-input">
    <span>{labelText}</span>
    <input type="text" value={defaultText} placeholder={placeholder}>
</div>
