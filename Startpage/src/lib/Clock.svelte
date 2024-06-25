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

<div id="bg">
    <div id="clock">
        <p>{hours}</p>
        <span class="separator"></span>
        <p>{minutes}</p>
    </div>
</div>

<style>

    #bg {
        background-image: url(../assets/wallpaper2.jpeg);
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        width: 40%;
        height: 64vh;
        display: flex;
        align-items: center;
        justify-content: center;

        border-radius: 5px;
    }

    #clock {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        width: 60%;
        height: 28vh;
        width: 10vw;
        border-radius: 5px;
        row-gap: 0.5rem;
        backdrop-filter: blur(10px);

        font-family: 'JetBrains Mono', monospace;
        
        border-radius: 0.5rem;
        font-size: var(--medium-font-size);

        background-color: #11111bd2;
        /*border: 2px solid #f5c2e7;*/
        /*box-shadow: 0 0 15px 15px var(--ui-background), inset 0 0 15px 15px var(--ui-background);*/
    }

    #clock p { 
        font-size: 2.7rem;
        margin-top: 1rem;
        margin-bottom: 1rem;
    }

    .separator {
        width: 20%;
        height: 3px;
        background-color: var(--accent);
        border-radius: 2px;
    }
</style>