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

<form on:submit={handleSubmit}>
    <input type="text" bind:value={query} placeholder="Search something on Google" />
    <button type="submit">Search</button>
</form>

<style>
    form {
        width: 110%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        column-gap: 1rem;
    }
    input {
        all: unset;
        font-size: var(--small-font-size);
        width: 80%;
        text-align: start;
        height: 1.5rem;
        padding: 0.7rem;
        padding-left: 1rem;
        padding-right: 1rem;
        border-radius: 5px;
        background-color: var(--ui-background);
    }

    button {
        all: unset;
        padding: 0.5rem;
        border-radius: 5px;
        color: var(--accent);
        background-color: #11111b;
        font-size: var(--small-font-size);
        width: 20%;
        cursor: pointer;
        border: 2px solid var(--accent);
    }

</style>
