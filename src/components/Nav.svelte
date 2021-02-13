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
        grid-template-columns: auto auto;
		list-style: none;
		padding-left: 20px;
		padding-right: 10px;
        width: -webkit-fill-available;
	}

    .title-box {
		text-transform: uppercase;
    }
    .title-box > h2 {
		margin: 0;
    }

    .switch-dark-mode {
		text-align: end;
    }

	.switch-dark-mode > h3 {
		display: inline-block;
		margin: 0;
		vertical-align: -webkit-baseline-middle;
	}
	@media only screen and (max-width: 768px){
		h2 {
			font-size: 1em;
		}
	}

	@media only screen and (max-width: 400px){
		h2 {
			font-size: 1em;
		}

		.switch-dark-mode {
			font-size: 12px;
		}
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
