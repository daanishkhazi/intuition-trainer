<script>
    import { onMount } from 'svelte' ;
    let w = 0;
    let h = 0;
    onMount (() => { 
        w = 1 + Math.random() * 4;
        h = 1 + Math.random() * 4;
     });
    let wg = 0;
    let hg = 0;
    let score = 0;
    function calculateScore (){
        let distance = 100 * (1 / (Math.sqrt(Math.pow(w - wg, 2) + Math.pow(h - hg, 2)) * 100));
        score = Math.round(200 * sigmoid(distance - .5));
    }
    function sigmoid(z) {
        return 1 / (1 + Math.exp(-z));
    }
    function resetGame() {
        w = 1 + Math.random() * 4;
        h = 1 + Math.random() * 4;
        wg = 0;
        hg = 0;
        score = 0;
    }
</script>

<div class="flex p-30">
    <div class=" flex flex-none justify-center w-8/12">
        <div style="width:{w}in; height:{h}in;" class="square"></div>
    </div>
    <div class="flex-auto w-4/12">
        <label for="wg"><b>Guess width:</b></label>
        <input id="wg" style="border-color:#216064" bind:value={wg}>
        <br>
        <label for="hg"><b>Guess height:</b></label>
        <input id="hg" style="border-color:#216064" bind:value={hg}>
        <br>
        {#if score === 0}
            <button on:click={calculateScore}>Check my Intuition</button>
        {:else}
            <h2> Visual IQ: {score} </h2>
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
</style>