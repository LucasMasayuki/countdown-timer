<script lang="ts">
  	import { onMount } from 'svelte';

	type State = {
		days: number,
		hours: number,
		minutes: number,
		seconds: number,
	}

	const now = new Date()
	export let eventTitle: String
	export let targetTime: Date
	export let timePassed = targetTime !== null ? Math.abs(targetTime.getTime() / 1000) - Math.abs(now.getTime() / 1000) : 0
	let state = initState()
	let prevTargetTime = targetTime
	let setIntervalVar: any

	$: {
		if (targetTime !== null && prevTargetTime.getTime() !== targetTime.getTime()) {
			timePassed = targetTime != null ? Math.abs(targetTime.getTime() / 1000) - Math.abs(now.getTime() / 1000) : 0
			state = initState()
			prevTargetTime = targetTime
		} else if (timePassed) {
			state = initState()
		}
	}

	onMount(() => {
		const supportNotification = 'Notification' in window

		if (supportNotification && Notification.permission !== 'denied' && Notification.permission !== 'granted') {
			Notification.requestPermission((permission) => {});
		}

	 	setIntervalVar	= setInterval(() => {
			state.seconds -= 1
			timePassed -= 1
			if (timePassed >= 1) {
				if (state.seconds == 0 && state.minutes != 0) {
					state.minutes -= 1
					state.seconds = 60
				}

				if (state.minutes == 0 && state.hours != 0) {
					state.hours -= 1
					state.minutes = 60
				}

				if (state.hours == 0 && state.days != 0) {
					state.days -= 1
					state.minutes = 24
				}
			} else {
				notify()
				clearInterval(setIntervalVar)
			}
		}, 1000)
	})

	function notify() {
		const supportNotification = 'Notification' in window
		if (supportNotification && Notification.permission === 'granted') {
			new Notification(`The time of the event is up ${eventTitle}`);
		}
	}

	function initState(): State {
		if (targetTime === null) {
			return {
				days: 0,
				hours: 0,
				minutes: 0,
				seconds: 0,
			}
		}

		// get total seconds between the times
		let delta = Math.abs(targetTime.getTime() - now.getTime()) / 1000

		// calculate (and subtract) whole days
		let days = Math.floor(delta / 86400)
		delta -= days * 86400

		// calculate (and subtract) whole hours
		let hours = Math.floor(delta / 3600) % 24
		delta -= hours * 3600

		// calculate (and subtract) whole minutes
		let minutes = Math.floor(delta / 60) % 60
		delta -= minutes * 60

		// what's left is seconds
		let seconds = Math.floor(delta % 60)

		return {
			days: days,
			hours: hours,
			minutes: minutes,
			seconds: seconds,
		}
	}

	function formatTime(time: number): String {
		if (time < 10) {
			return `0${time}`
		}

		return `${time}`
	}
</script>

<style>
	.countdown-container {
		display: inline-grid;
		grid-template-columns: auto auto auto auto auto auto auto;
		grid-gap: 2em
	}

	.countdown-cell {
		text-align: center;
	}

	.countdown-separator {
		font-size: larger;
		font-weight: bold;
	}

	.number {
		font-weight: bold;
		font-size: 38px;
	}

	.label {
		text-transform: uppercase;
	}

	.line {
		border-bottom: 1px solid black;
		height: 1px;
		margin: 1em 0;
		width: 5em
	}

	.title-content {
		margin-bottom: 5em;
	}

	@media only screen and (max-width: 768px){
		.countdown-container {
			grid-gap: 0.55em
		}

		.line {
			border-bottom: 1px solid black;
			height: 1px;
			margin: 1em 0;
			width: 4em
		}

		.number {
			font-weight: bold;
			font-size: 28px;
		}
	}

	@media only screen and (max-width: 400px){
		.countdown-container {
			grid-gap: 0.25em
		}

		.line {
			border-bottom: 1px solid black;
			height: 1px;
			margin: 1em 0;
			width: 4em
		}

		.number {
			font-weight: bold;
			font-size: 20px;
		}
	}
</style>

<div class="title-content">
	<h1>{eventTitle}</h1>
</div>
<div class="countdown-container">
	<div class="countdown-cell">
		<span class="number">{formatTime(state.days)}</span>
		<div class="line"></div>
		<span class="label">Days</span>
	</div>
	<div class="countdown-separator">
		:
	</div>
	<div class="countdown-cell">
		<span class="number">{formatTime(state.hours)}</span>
		<div class="line"></div>
		<span class="label">Hours</span>
	</div>
	<div class="countdown-separator">
		:
	</div>
	<div class="countdown-cell">
		<span class="number">{formatTime(state.minutes)}</span>
		<div class="line"></div>
		<span class="label">Minutes</span>
	</div>
	<div class="countdown-separator">
		:
	</div>
	<div class="countdown-cell">
		<span class="number">{formatTime(state.seconds)}</span>
		<div class="line"></div>
		<span class="label">Seconds</span>
	</div>
</div>
