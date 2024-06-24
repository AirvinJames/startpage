<script>
    let query = '';

    function handleSubmit(event) {
        event.preventDefault();
        if (query.trim()) {
            const googleSearchUrl = `https://www.google.com/search?q=${encodeURIComponent(query)}`;
            window.location.href = googleSearchUrl;
        }
    }
</script>

<main>
    <form on:submit={handleSubmit}>
        <input type="text" bind:value={query} placeholder="Search something on Google" />
        <button type="submit">Search</button>
    </form>
</main>

<style>
    main {
        text-align: center;
        width: 100%;
    }
    input {
        margin-right: 0.5em;
        font-size: var(--small-font-size);
    }
</style>
