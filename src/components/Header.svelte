<script>
    import SwitchButton from './SwitchButton.svelte'
    export let title
    let darkMode = false;
</script>

<style>
    .header {
        background-color: royalblue;
        color: white;
        display: inline-grid;
        grid-template-columns: 85% 15%;
        padding: 0.10em;
        width: 100%;
    }
    .title-box {
        margin-left: 15px;
    }
    .switch-dark-mode {
        align-items: center;
        display: inline-grid;
        float: right;
        grid-template-columns: auto auto;
    }
</style>

<header class="header">
    <div class="title-box">
        <h2>{title}</h2>
    </div>
    <div class="switch-dark-mode">
        <h3>dark mode</h3>
        <SwitchButton bind:checked={darkMode} />
    </div>
</header>
