<script>
    import { onMount } from 'svelte';

    // Actual dimensions
    let w = 0;
    let h = 0;

    // User guesses
    let wg = 0;
    let hg = 0;

    // Variables for displaying results
    let score = 0;
    let diffW = 0;
    let diffH = 0;
    let absDiffW = 0;
    let absDiffH = 0;
    let directionW = '';
    let directionH = '';

    // Initialize the game with random dimensions
    onMount(() => {
        w = 1 + Math.random() * 4; // Width between 1 and 5 inches
        h = 1 + Math.random() * 4; // Height between 1 and 5 inches
    });

    function calculateScore() {
        // Calculate differences
        diffW = wg - w;
        diffH = hg - h;

        // Determine if guesses were too big or too small
        directionW = diffW > 0 ? 'too big' : 'too small';
        directionH = diffH > 0 ? 'too big' : 'too small';

        // Absolute differences for display
        absDiffW = Math.abs(diffW).toFixed(2);
        absDiffH = Math.abs(diffH).toFixed(2);

        // Calculate percentage errors
        let percentErrorWidth = (Math.abs(diffW) / w) * 100;
        let percentErrorHeight = (Math.abs(diffH) / h) * 100;

        // Mean percentage error
        let meanError = (percentErrorWidth + percentErrorHeight) / 2;

        // Scoring function using exponential decay
        let k = Math.log(2) / 50; // Controls the rate of decay
        score = Math.round(100 * Math.exp(-k * meanError));

        // Ensure the score doesn't go below 0
        score = Math.max(0, score);
    }

    function resetGame() {
        w = 1 + Math.random() * 4;
        h = 1 + Math.random() * 4;
        wg = 0;
        hg = 0;
        score = 0;
        diffW = 0;
        diffH = 0;
        absDiffW = 0;
        absDiffH = 0;
        directionW = '';
        directionH = '';
    }
</script>

<div class="flex p-30">
    <div class="flex flex-none justify-center w-8/12">
        <div style="width:{w}in; height:{h}in;" class="square"></div>
    </div>
    <div class="flex-auto w-4/12">
        <label for="wg"><b>Guess width (in inches):</b></label>
        <input id="wg" type="number" min="0" step="0.01" bind:value={wg}>
        <br>
        <label for="hg"><b>Guess height (in inches):</b></label>
        <input id="hg" type="number" min="0" step="0.01" bind:value={hg}>
        <br>
        {#if score === 0}
            <button on:click={calculateScore}>Check my Intuition</button>
        {:else}
            <h2>Visual IQ: {score} / 100</h2>
            <p>Your width guess was {absDiffW} inches {directionW}.</p>
            <p>Your height guess was {absDiffH} inches {directionH}.</p>
            <button on:click={resetGame}>Try again</button>
        {/if}
    </div>
</div>

<style>
    .square { 
        background-color: #293952;
    } 
    
    button {
        background-color: #293952;
        color: white;
        border: none;
        border-radius: 4px;
        padding: 10px;
        font-size: 1.2em;
        cursor: pointer;
        margin-top: 2em;
        margin-bottom: .5em;
    }

    input {
        border: 1px solid #216064;
        border-radius: 4px;
        padding: 5px;
        margin-bottom: 1em;
        width: 100%;
    }

    label {
        display: block;
        margin-top: 1em;
    }

    .flex {
        display: flex;
        flex-wrap: wrap;
    }

    .p-30 {
        padding: 30px;
    }

    .w-8\/12 {
        width: 66.666667%;
    }

    .w-4\/12 {
        width: 33.333333%;
    }
</style>
