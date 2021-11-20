<script>
    let simpleParityA = '';
	let simpleParityB = '';
	let outputA = '';
	let outputB = '';

	function isValidBinary(input) {
		for (let i of input) {
			if (i !== '0'&& i != '1') {
				return false;
			}
		}
		return true;
	}

	function generateParity(input) {
		let sum = 0;

		for (let i of input) {
			if (i === 1) {
				sum++;
			}
		}
		let parity = sum%2 === 0 ? '0' : '1';
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

				outputA = dataWord;
				outputB = syndromeCheck === true ? simpleParityB.substring(
					0, simpleParityB.length-2) : 'Discarded';

				// console.log('parity', parityA);
				// console.log(simpleParityA);
				// console.log(simpleParityB);
				// console.log('output', outputA);
				// console.log('output', outputB);
			} else {
				console.log('hatdog');
			}
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

    <p>Output A: { outputA }</p>
	<p>Output B: { outputB }</p>
</div>

<style>
	.card {
		display: flex;
		flex-direction: column;
		background-color: #e5f7f6;
		padding: 16px;
		border-radius: 20px;
		height: 400px;
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
</style>