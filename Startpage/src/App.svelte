<script>
    import { onMount } from 'svelte';

	let date = new Date();

	$: hours = date.getHours();
	$: minutes = date.getMinutes();

    let monthLookUpTable = {
        0: "January",
        1: "February",
        2: "March",
        3: "April",
        4: "May",
        5: "June",
        6: "July",
        7: "August",
        8: "September",
        9: "October",
        10: "November",
        11: "December"
    };

    $: day = date.getDate();
    $: month = date.getMonth();
    $: year = date.getFullYear();
    $: monthName = monthLookUpTable[month];
    

	onMount(() => {
		const interval = setInterval(() => {
			date = new Date();
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<div id="day-info">
    <div id="clock">
        <p>{hours}</p>
        <span class="separator"></span>
        <p>{minutes}</p>
    </div>

    <p id="date">{monthName} {day}, {year}</p>
</div>

<style>
    :root {
        --text-color: #cdd6f4;
        --ui-background: #1e1e2e;
        --transparent-overlay: #11111b56;
    }
    #day-info {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 1rem;
        height: 70vh;
        width: 10vw;
        border-radius: 0.5rem;

        background-color: var(--ui-background);
    }

    #clock {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: var(--transparent-overlay);
        width: 60%;
    }

    .separator {
        width: 50%;
        height: 2px;
        background-color: var(--text-color);
        border-radius: 2px;
    }
</style>