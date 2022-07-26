<script>
	import PlayerScore from "./components/playerScore.svelte";

	let player1Score = 0;
	let player2Score = 0;
	
	function reset() {
		player1Score = 0;
		player2Score = 0;
	}
</script>

<main>
	<div class="header">
		<h1>Player score app</h1>
		<button on:click={reset}>Reset</button>
	</div>
	<div class="player-card">
		<PlayerScore bind:playerScore={player1Score} playerName="Player 1" />
		<PlayerScore bind:playerScore={player2Score} playerName="Player 2" />
	</div>
</main>

<style>
	:global(*) {
		margin: 0 !important;
		padding: 0 !important;
		box-sizing: border-box !important;
	}

	main {
		max-width: 60rem;
		min-height: 100vh;
		margin: 0 auto !important;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 4rem;
		text-align: center;
	}
	
	.header {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.header button {
		width: 6.5rem;
	}

	.player-card {
		width: 40rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
</style>