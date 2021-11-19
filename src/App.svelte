<script>
	import SimpleParityCard from './cards/SimpleParityCard.svelte';
	import TwoDimensionalCard from './cards/TwoDimensionalCard.svelte';
	import ChecksumCard from './cards/ChecksumCard.svelte';
	import CyclicCard from './cards/CyclicCard.svelte';
</script>

<main>
	<div class="header">
		<h1>
			Lab Exercise 7: Error Detection Techniques
		</h1>
		<h2>
			Patricia Lexa U. Tumulak
		</h2>
		<hr>
	</div>
	
	<div class="body">
		<SimpleParityCard />
		<TwoDimensionalCard />
		<ChecksumCard />
		<CyclicCard />
	</div>
</main>

<style>
	/* // COLORS

	// $primary: #0000;
	// $secondary: #444F54;
	// $tertiary: #72838C;
	// $yellow: #F5C023;
	// $violet: #8B02D3;
	// $orange: #F4A259;
	// $pink: #ED64A6;
	// $teal: #38B2AC;
	// $indigo: #667EEA; */

	main {
		margin: auto;
		width: 50%;
	}
	.header {
		text-align: center;
		padding: 1em;
	}

	.body {
		display: grid;
		grid-template-columns: 1fr 1fr;
		row-gap: 10px;
		column-gap: 10px;
	}

	h1 {
		color: #38B2AC;
		font-size: 2em;
		font-weight: 400;
	}

	h2 {
		font-size: 1.5em;
		font-weight: 300;
	}
	
	hr {
		width: 100%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>