<script>
    import Clock from "./lib/Clock.svelte";
    import Search from "./lib/Search.svelte";
    import { onMount } from 'svelte';

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

    let date = new Date();

    $: day = date.getDate();
    $: month = date.getMonth();
    $: year = date.getFullYear();
    $: monthName = monthLookUpTable[month];

    // Variable that gives "Morning", "Afternoon", or "Evening" based on time of day
    $: timeOfDay = date.getHours() < 12 ? "Morning" : date.getHours() < 18 ? "Afternoon" : "Evening";

    onMount(() => {
		const interval = setInterval(() => {
			date = new Date();
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});

    let name = "Airvin";
</script>

<main>
    <Clock />

    <div class="side-container">
        <h1>Good {timeOfDay}, {name}!</h1>
        <p>Today is {monthName} {day}, {year}</p>
        
        <Search />
    </div>
</main>

<style>
    :root {
        --text-color: #cdd6f4;
        --ui-background: #1e1e2e;
        --transparent-overlay: #11111b56;

        --large-font-size: 2.5rem;
        --medium-font-size: 2rem;
        --small-font-size: 1.3rem;
    }
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        column-gap: 5rem;

        font-family: 'JetBrains Mono', monospace;
        color: var(--text-color);
    }

    h1 {
        font-size: var(--large-font-size);
    }

    .side-container {
        display: flex;
        flex-direction: column;
        align-items: start;
    }
</style>