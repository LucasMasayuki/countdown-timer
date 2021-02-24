<script lang="ts">
    import { theme } from '../shared/store';
  	import { onMount } from 'svelte';

    let themeMode: string;
    let checked: boolean;

    onMount( () => {
      themeMode = window.localStorage.getItem('theme') ?? 'light'
      checked = themeMode === 'dark'

      if (checked) {
        window.document.body.classList.toggle('dark-mode')
      }

      theme.update(() => themeMode)
    });

    theme.subscribe(() => {
      checked = themeMode === 'dark'
    })

    function onChangeSwitchDarkMode() {
      const themeMode = !checked ? 'dark' : 'light'
      window.document.body.classList.toggle('dark-mode')
      theme.update(() => themeMode)
      window.localStorage.setItem('theme', themeMode)
    }
</script>

<style>
    .switch {
      position: relative;
      display: inline-block;
      width: 60px;
      height: 34px;
    }

    .switch input {
      opacity: 0;
      width: 0;
      height: 0;
    }

    .slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: #ccc;
      -webkit-transition: 0.4s;
      transition: 0.4s;
      border-radius: 34px;
    }

    .slider:before {
      position: absolute;
      content: "";
      height: 26px;
      width: 26px;
      left: 4px;
      bottom: 4px;
      background-color: white;
      -webkit-transition: 0.4s;
      transition: 0.4s;
      border-radius: 50%;
    }

    input:checked + .slider {
      background-color: #4CD869;
    }

    input:checked + .slider {
      box-shadow: 0 0 1px #4CD869;
    }

    input:checked + .slider:before {
      -webkit-transform: translateX(26px);
      -ms-transform: translateX(26px);
      transform: translateX(26px);
    }


    @media only screen and (max-width: 768px){
      .switch {
        width: 40px;
        height: 26px;
      }

      .slider:before {
        height: 16px;
        width: 16px;
      }

      input:checked + .slider:before {
        -webkit-transform: translateX(16px);
        -ms-transform: translateX(16px);
        transform: translateX(16
        px);
      }

    }
</style>

<label class="switch">
    <input on:change={onChangeSwitchDarkMode}  type="checkbox" bind:checked />
    <span class="slider" />
</label>
