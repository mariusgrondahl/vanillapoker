	<script>
	let cards = [];

	const kortstokk = ['1r', '2r', '3r', '5r', '6r', '7r', '8r', '9r', 'tr', 'jr', 'qr', 'kr','er', '1s', 
	'2s', '3s', '5s', '6s', '7s', '8s', '9s', 'ts', 'js', 'qs', 'ks','es', '1h', '2h', '3h', '5h', '6h', 
	'7h', '8h', '9h', 'th', 'jh', 'qh', 'kh','eh', '1k', '2k', '3k', '5k', '6k', '7k', '8k', '9k', 'tk', 
	'jk', 'qk', 'kk','ek'];

	function pickCard(){
		const valgtkort = kortstokk[Math.floor(Math.random()*kortstokk.length)]

		if (cards.length >= 5) {
			console.log("Du kan ikke velge flere kort")
		} else {
			cards.push(valgtkort)
			cards = cards
		}
	}

	function newHand(){
		cards = []
		cards = cards
	}
</script>

<h1>Velkommen til Poker NM</h1>
<p>Du har {cards.length} kort på hånda</p>

<ul>
<li>{cards}</li>
</ul>

<button on:click={pickCard}>Trekk kort</button>
<button on:click={newHand}>Kast hånd</button>
