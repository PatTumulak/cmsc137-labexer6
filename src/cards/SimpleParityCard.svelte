<script>
    let simpleParityA = '';
	let simpleParityB = '';
	$:outputA = '';
	$:outputB = '';

	function isValidBinary(input) {
		for (let i of input) {
			if (i !== '0'&& i != '1') {
				return false;
			}
		}
		return true;
	}

	function generateParity(input) {
		console.log('input', input)
		let sum = 0;

		for (var i of input) {
			if (i === '1') {
				sum++;
			}
		}
		// console.log('sum', sum)
		let parity = sum%2 === 0 ? '0' : '1';
		// console.log('parity', parity);
		return parity;
	}

	function getParityBit(input) {
		// console.log('parity bit', input[input.length - 1]);
		return input[input.length - 1];
	}

	function checkSyndrome(input) {
		let receivedParity = getParityBit(input);
		let neededParity = generateParity(input.substring(0, input.length-1));

		// console.log('lol', input.substring(0, input.length-1));

		return receivedParity === neededParity ? true : false;
	}

	function handleClick() {
		if (simpleParityB && simpleParityA) {
			let inputValidityA = isValidBinary(simpleParityA) 
				&& simpleParityA.length === 8 ? true : false;
			let inputValidityB = isValidBinary(simpleParityB) 
				&& simpleParityB.length === 9 ? true : false;

			if (inputValidityA && inputValidityB) {
				// input A stuff
				// generates the parity bit
				let parityA = generateParity(simpleParityA);
				let dataWord = simpleParityA + parityA;	
				
				// input B stuff
				// checks the parity bit and generates an actual parity bit to
				// compare
				let syndromeCheck = checkSyndrome(simpleParityB);

				outputA = '@Sender: ' + dataWord;
				outputB = '@Receiver: ' + (syndromeCheck === true ? 
					simpleParityB.substring(0, simpleParityB.length-1) : 
					'Discarded');

				// console.log('parity', parityA);
				// console.log(simpleParityA);
				// console.log(simpleParityB);
				// console.log('output', outputA);
				// console.log('output', outputB);
			} else {
				outputA = 'Invalid input';
				outputB = 'Invalid input';
			}
		} else {
			outputA = 'No input';
			outputB = 'No input';
		}
	}
</script>

<div class="card">
    <h3>
        A. Simple Parity Check (Even Parity)
    </h3>
    <p>Data Word (8-bit)</p>
    <input type="text" bind:value={simpleParityA}>

    <p>Code Word (8-bit and Parity bit)</p>
    <input type="text" bind:value={simpleParityB}>

    <button on:click={handleClick}>Check</button>
	
	<div class="output">
		<span class="output-row">
			<p>Output A:</p> 
			{#if outputA}
				<p class="output-tag">{outputA}</p>
			{:else}
				<p></p>
			{/if}
		</span>
		<span class="output-row">
			<p>Output B:</p> 
			{#if outputB}
				<p class="output-tag">{outputB}</p>
			{:else}
				<p></p>
			{/if}
		</span>
	</div>
</div>

<style>
	.card {
		display: flex;
		flex-direction: column;
		background-color: #e5f7f6;
		padding: 16px;
		border-radius: 20px;
		height: 390px;
		box-shadow: 1px 3px 10px rgb(0 0 0 / 0.2);
	}
	
	input {
		border-radius: 5px;
	}

    button {
		margin-top: 10px;
		width: 100px;
		color: white;
		background-color: #38B2AC;
		border-radius: 7px;
	}

	button:hover {
		cursor: pointer;
		background-color: #57d1cb;
	}

	.output {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		height: 5px;
	}

	.output-row {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 1px;
	}

	p {
		margin: 0;
		padding: 10px 0;
	}
	
	.output-tag {
		margin-left: 10px;
		padding: 5px 10px;
		border-radius: 6px;
		background-color: aquamarine;
	}
</style>
