<script lang="ts">
    import SwitchButton from './SwitchButton.svelte'

	let title = 'Countdown timer'
</script>

<style>
	nav {
        background-color: royalblue;
        color: white;
	}
	ul {
		align-items: center;
        display: inline-grid;
        grid-template-columns: 85% 15%;
        width: -webkit-fill-available;
	}

	ul {
		list-style: none;
	}

    .title-box {
		text-transform: uppercase;
    }
    .title-box > h2 {
		margin: 0;
    }

    .switch-dark-mode {
        align-items: center;
        display: inline-grid;
        float: right;
        grid-template-columns: auto auto;
    }

	.switch-dark-mode > h3 {
		margin: 0;
	}

</style>

<nav>
	<ul>
		<li class="title-box">
			<h2>{title}</h2>
		</li>
		<li class="switch-dark-mode">
			<h3>dark mode</h3>
			<SwitchButton />
		</li>
	</ul>
</nav>
