<script>
	import Countdown from '../components/Countdown.svelte';
	import Input from '../components/Input.svelte';
	import { beforeUpdate, onMount } from 'svelte';
	const now = new Date()

	let targetTime = defaultDate()
	let eventTitle = 'Time to tomorrow'
	let date = `${targetTime.getUTCFullYear()}-${formatLeadingZero(targetTime.getMonth() + 1)}-${targetTime.getDate()}`
	let time = `${formatLeadingZero(targetTime.getHours())}:${formatLeadingZero(targetTime.getMinutes())}:${formatLeadingZero(targetTime.getSeconds())}`
	let minDate = `${now.getUTCFullYear()}-${formatLeadingZero(now.getMonth() + 1)}-${now.getDate()}`
	let minTime = `${formatLeadingZero(now.getHours())}:${formatLeadingZero(now.getMinutes())}:${now.getSeconds()}`
	let errorMessage = ''

	function defaultDate() {
		const tomorrow = new Date(now)
		tomorrow.setDate(now.getDate() + 1)
		tomorrow.setHours(0)
		tomorrow.setMinutes(0)
		tomorrow.setSeconds(0)
		return tomorrow
	}

	function formatLeadingZero(time) {
  		return (time < 10 ? '0' : '') + time;
	}

	function onFocusOutEventTitle(e) {
		eventTitle = e.currentTarget.value
		window.localStorage.setItem('eventTitle', eventTitle)
	}

	function onFocusOutTargetTime(e) {
		time = e.currentTarget.value
		targetTime = new Date(`${date} ${time}`)
		window.localStorage.setItem('eventTime', time)
	}

	function onFocusOutDate(e) {
		date = e.currentTarget.value
		targetTime = new Date(`${date} ${time}`)
		window.localStorage.setItem('eventDate', date)
	}

	function updateCountdown() {
		targetTime = new Date(`${date} ${time}`)

		if (targetTime.getTime() < now.getTime()) {
			targetTime = null
			errorMessage = "put a date longer than today's date"
		} else {
			errorMessage = ''
		}
	}

	onMount(() => {
		const localstorageEventName = window.localStorage.getItem('eventTitle')
		const localstorageEventTime = window.localStorage.getItem('eventTime')
		const localstorageEventDate = window.localStorage.getItem('eventDate')

		eventTitle = localstorageEventName != undefined ? localstorageEventName : eventTitle
		time = localstorageEventTime != undefined ? localstorageEventTime : time
		date = localstorageEventDate != undefined ? localstorageEventDate : date

		updateCountdown()
	});

	beforeUpdate(() => {
		updateCountdown()
	})
</script>

<style>
	.countdown {
		text-align: center;
	}

	.grid-view {
		display: grid;
		grid-template-columns: auto auto auto;
		grid-gap: 3em;
		margin-bottom: 2em;
	}

	.coutdown-input-container {
		margin-top: 1em;
		padding: 2em;
	}

	@media only screen and (max-width: 768px){
		.grid-view {
			grid-template-columns: auto;
		}
	}
</style>

<svelte:head>
	<title>Countdown timer</title>
</svelte:head>

<div class="countdown">
	<Countdown targetTime={targetTime} eventTitle={eventTitle}/>
</div>

<div class="coutdown-input-container">
	<h2>Setup</h2>
	<div class="grid-view">
		<Input id="svelte-event-name" type="text" labelText="Event name" placeholder="Event name" value={eventTitle} onFocusOut={onFocusOutEventTitle}/>
		<Input id="svelte-date" type="date" labelText="Date" onFocusOut={onFocusOutDate} value={date} min={minDate} errorMessage={errorMessage} />
		<Input id="svelte-optional-time" type="time" labelText="Time (optional)" value={time} onFocusOut={onFocusOutTargetTime} min={minTime} errorMessage={errorMessage}/>
	</div>
</div>
