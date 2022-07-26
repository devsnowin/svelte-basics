<script>
    export let playerName;

    export let playerScore = 0;

    const updateScore = () => {
        playerScore += 1;
    };

    const decreaseScore = () => {
        playerScore > 0 && (playerScore -= 1);
    };

    export const reset = () => {
        playerScore = 0
    }
    
</script>

<div class="player-container">
    <h1>{playerName}</h1>
    <p>{playerScore}</p>
    <button on:click={updateScore}>Up</button>
    <button on:click={decreaseScore}>Down</button>
</div>

<style>
    .player-container{
        max-width: 40rem;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 2rem;
    }
</style>
