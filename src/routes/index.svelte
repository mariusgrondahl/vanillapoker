	<script>
	let cards = [];

	let winmessage = "Du har ikke gode kort på hånden"

	const kortstokk = ['1r', '2r', '3r', '5r', '6r', '7r', '8r', '9r', 'tr', 'jr', 'qr', 'kr','er', '1s', 
	'2s', '3s', '5s', '6s', '7s', '8s', '9s', 'ts', 'js', 'qs', 'ks','es', '1h', '2h', '3h', '5h', '6h', 
	'7h', '8h', '9h', 'th', 'jh', 'qh', 'kh','eh', '1k', '2k', '3k', '5k', '6k', '7k', '8k', '9k', 'tk', 
	'jk', 'qk', 'kk','ek'];

	function checkPar(cards = []) {
		let count = 0;

		cards.sort()
		for(let i = 0; i < cards.length; i++){
			if(cards[i] === cards[i + 1]){
				i++;
				count++;
			}
		}
		return count;
	};

	function check3(cards = []) {
		let count = 0;

		cards.sort()
		for(let i = 0; i < cards.length; i++){
			if(cards[i + 1] === cards[i]){
				i++;
				count++;
			}
		}
		return count;
	};


	function pickCard(){
		const valgtkort = kortstokk[Math.floor(Math.random()*kortstokk.length)]
		if (cards.length >= 5) {
			return
		} else {
			cards.push(valgtkort)
			cards = cards
		}

		winningHand()
	}

	function newHand(){
		cards = []
		cards = cards
		winmessage = "Du har ikke gode kort på hånden"
	}


	function winningHand() {
		let first = cards.map(function(card) {
			 return(card[0])
		});

		let second = cards.map(function(card) {
			return(card[1])
		});	

			console.log(check3(first))
		// checking 
		if (checkPar(first) === 1)  {
			winmessage = "Du har 1 par på hånden";
		} else if (checkPar(first) === 2)  {
			winmessage = "Du har 4 like på hånden";
		} else if (checkPar(first) === 2) {
			winmessage = "Du har 4 like";
		}
	}

</script>
<div class="poker">
<h1>Amedia Poker NM</h1>
 {#if cards.length < 5} 
 <p>Du har <span class="bold">{cards.length}</span> kort på hånda.</p>
 {:else}
 <p>Du har <span class="bold">5</span> kort på hånda og kan ikke trekke flere</p>
 {/if}


<ul class="cards">
	{#each cards as card}
		<li>{card}</li>
	{/each}
</ul>

 {#if cards.length < 5} 
 <p>{winmessage}.</p>
 {:else}
<p>{winmessage}.</p>
 {/if}


</div>
<div class="control-panel">
<button class="cta" on:click={pickCard}>Trekk kort</button>
<button class="clear" on:click={newHand}>Kast hånd</button>
</div>

<style>
	.poker{
		color: white;
		max-width: 1280px;
		margin: 0 auto;
		position: relative;
		padding-top: 50px;
		text-align: center;

	}
	.cards{
		position: relative;
		list-style: none;
		display: flex;
		flex-direction: row;
		justify-content: center;
		width: 100%;
		margin-top: 30px;
		padding:0;
	}

	ul li{
		min-width: 100px;
		max-width: 100px;
		min-height: 200px;
		background: white;
		border-radius: 10px;
		color: #2d2d2d;
		display: flex;
		justify-content: center;
		padding: 20px;
		margin: 10px;
		font-size: 30px;
		font-weight: bold;
	}

	.control-panel{
		position: absolute;
		width: 100vw;
		background: none;
		bottom: 50px;
		padding: 20px;
		box-sizing: border-box;
		display: flex;
		justify-content: center;
	}
	
	button{
		padding: 15px 25px;
		border-radius: 10px;
		font-size: 16px;
		border: none;
		outline: none;
		background: goldrod;
		margin: 0px 10px;
		color: #2d2d2d;
	}

	button.cta{
		background: gold;
	}

	button.clear{
		background: tomato;
	}



</style>
