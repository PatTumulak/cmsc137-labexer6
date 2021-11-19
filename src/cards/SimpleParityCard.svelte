<script>
    let simpleParityA = '';
	let simpleParityB = '';

	function isValidBinary(input) {
		for (let i of input) {
			if (i !== '0'&& i != '1') return false;
		}
		return true;
	}

	function handleClick() {
		if (simpleParityB && simpleParityA) {
			let inputValidityA = isValidBinary(simpleParityA) 
				&& simpleParityA.length === 8 ? true : false;
			let inputValidityB = isValidBinary(simpleParityB) 
				&& simpleParityB.length === 9 ? true : false;

			if (inputValidityA && inputValidityB) {
				console.log(simpleParityA);
				console.log(simpleParityB);
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

    <p>Output</p>
    <p></p>
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