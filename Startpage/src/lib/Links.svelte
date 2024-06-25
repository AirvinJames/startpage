<script>
    import { House, BriefcaseBusiness, BookMarked,
    Youtube, Facebook, Music, Swords, AtSign, SquareLibrary, CodeXml,
    BotMessageSquare, BookText, Paintbrush, Github, Wrench } from 'lucide-svelte';

    let currentSection = 'home';

    function selectSection(section) {
        currentSection = section;
    }
</script>

<div class="main">
    <section>
        <div class="links">
            {#if currentSection === 'home'}
                <!--<h2>Home</h2>-->
                <ul>
                    <li id="spotify"><a href="https://www.spotify.com"><Music />Spotify</a></li>
                    <li id="facebook"><a href="https://www.facebook.com"><Facebook />Facebook</a></li>
                    <li id="youtube"><a href="https://www.youtube.com"><Youtube />YouTube</a></li>
                    <li id="chess"><a href="https://www.chess.com"><Swords />Chess</a></li>
                </ul>
            {/if}
            {#if currentSection === 'school'}
                <!--<h2>School</h2>-->
                <ul>
                    <li id="docs"><a href="https://www.docs.google.com"><BookText />Google Docs</a></li>
                    <li id="chatgpt"><a href="https://www.chat.openai.com"><BotMessageSquare />ChatGPT</a></li>
                    <li id="classroom"><a href="https://www.classroom.google.com"><SquareLibrary />GClassroom</a></li>
                    <li id="codechum"><a href="https://batstate-u.codechum.com/"><CodeXml />CodeChum</a></li>
                </ul>
            {/if}
            {#if currentSection === 'hobbies'}
                <!--<h2>Hobbies</h2>-->
                <ul>
                    <li id="roguelikedev"><a href="https://www.reddit.com/r/roguelikedev"><AtSign />r/roguelikedev</a></li>
                    <li id="unixporn"><a href="https://www.reddit.com/r/unixporn"><Paintbrush />r/unixporn</a></li>
                    <li id="github"><a href="https://www.github.com"><Github />GitHub</a></li>
                    <li id="game-jams"><a href="https://itch.io/jams"><Wrench />Game Jams</a></li>
                </ul>
            {/if}
        </div>
    </section>

    <nav>
        <button class:selected={currentSection === 'home'} on:click={() => selectSection('home')}><House /></button>
        <button class:selected={currentSection === 'school'} on:click={() => selectSection('school')}><BriefcaseBusiness /></button>
        <button class:selected={currentSection === 'hobbies'} on:click={() => selectSection('hobbies')}><BookMarked /></button>
    </nav>
</div>

<style>
    .main {
        display: flex;
        flex-direction: column;
        align-items: start;
        justify-content: center;
        width: 110%;
        height: 100%;

        border-radius: 5px;

        background-color: var(--ui-background);
    }  

    section {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        width: 100%;

    }

    ul {
        margin-top: 2rem;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        gap: 1rem;
        padding: 1rem;
    }
    nav {
        display: flex;
        justify-content: space-evenly;

        width: 100%;
        margin-top: 2rem;

        background-color: var(--transparent-overlay);
    }

    button {
        all: unset;
        padding: 1rem;
        cursor: pointer;
        width: 100%;
        transition: background-color 0.2s ease-in-out;
        border-top: 2px solid var(--ui-background);

        & svg > * {
            stroke: #7f849c;
            transition: stroke 0.2s ease-in-out;
            
        }
    }

    button:hover {
        background-color: var(--transparent-overlay);

        & svg > * {
            stroke: var(--text-color);
        }
    }

    /*h2 {
        font-size: var(--large-font-size);
        font-weight: 400;
    }*/

    li {
        display: flex;
        align-items: center;
        justify-content: center;

        transition: scale 0.2s ease-in-out, opacity 0.2s ease-in-out;
    }

    a {
        text-decoration: none;
        color: #cdd6f4;
        padding: 1rem;
        padding-left: 1.2rem;
        padding-right: 1.2rem;

        border-radius: 5px;

        min-width: 10rem;
        
        background-color: #11111be7;

        transition: background-color 0.2s ease-in-out;
        font-size: var(--medium-font-size);
        
        display: flex;
        align-items: center;
        justify-content: center;
        column-gap: 1.8rem;

        &:hover {
            background-color: #11111b;
        }

        & svg > * {
            transition: stroke 0.2s ease-in-out;
            max-height: 0.5rem;
            stroke:  	#a6d189;
        }
    }

    ul:has(li:hover) > li:not(:hover) {
        scale: 0.96;
        opacity: 0.85;
    }
    
    .selected {
        background-color: #11111bab;
        border-top: 2px solid var(--accent);

        & svg > * {
            stroke: var(--text-color);
        }
    }
    
    /*#facebook a {
        & svg > * {
            stroke:#1e66f5f3;
        }
    }

    #chess a {
        & svg > * {
            stroke:#40a02b;
        }
    }

    #spotify a {
        & svg > * {
            stroke:#1DB954;
        }
    }

    #youtube a {
        & svg > * {
            stroke:#f38ba8;
        }
    }*/
</style>
