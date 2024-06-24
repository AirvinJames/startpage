<script>
    import { onMount } from 'svelte';

	let date = new Date();

	$: hours = date.getHours().toString().padStart(2, "0");
	$: minutes = date.getMinutes().toString().padStart(2, "0");
    
	onMount(() => {
		const interval = setInterval(() => {
			date = new Date();
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<div id="clock">
    <p>{hours}</p>
    <span class="separator"></span>
    <p>{minutes}</p>
</div>

<style>
    :root {
        --text-color: #cdd6f4;
        --ui-background: #1e1e2e;
        --transparent-overlay: #11111b56;

        --large-font-size: 5rem;
        --medium-font-size: 3rem;
        --small-font-size: 1.5rem;
    }


    #clock {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 90%;
        height: 50vh;
        width: 10vw;
        font-size: 3.2rem;

        font-family: 'JetBrains Mono', monospace;
        
        border-radius: 0.5rem;
        font-size: var(--medium-font-size);

        background-color: var(--ui-background);
    }

    #clock p { 
        margin-top: 4rem;
        margin-bottom: 4rem;
    }

    .separator {
        width: 20%;
        height: 3px;
        background-color: var(--text-color);
        border-radius: 2px;
    }
</style>