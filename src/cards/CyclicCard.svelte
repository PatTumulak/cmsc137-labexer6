<script>
    let cyclicInput = '';
	let output = '';

	function isValidBinary(input) {
		for (let i of input) {
			if (i !== '0'&& i != '1') {
				return false;
			}
		}
		return true;
	}

	function xOR(remainder, divisor) {
		let or = '';

		for (let i = 0; i < 4; i++) {
			if (remainder[i] != divisor[i]) {
				or += '1';
			} else {
				or += '0';
			}
		}
		return or.substring(1,4);
	}

	function getRemainder(input) {
		return input.substring(input.length-3, input.length)
	}

	function getMessage(input) {
		return input.substring(0, 4);
	}

	function divideMk(dividend) {
		// won't be including the quotient since it is 
		// not really needed for this operation
		dividend += '000';
		let divisor = '';
		let remainder = dividend.substring(0, 3);

		// starts at the 4th bit
		for (let i = 3; i < 7; i++){
			remainder += dividend[i];
			divisor = remainder[0] === '0' ? '0000' : '1011';
			remainder = xOR(remainder, divisor);
		}

		return remainder;
	}

	function handleClick() {
		if (cyclicInput) {
			let isInputValid = cyclicInput.length === 7 && isValidBinary(cyclicInput);

			if (isInputValid) {
				let checkWord = getRemainder(cyclicInput);
				let message = getMessage(cyclicInput);
				let remainder = divideMk(message);

				if (checkWord === remainder) {
					output = 'Accept data';
				} else {
					output = 'CRC error detected';
				}
			} else {
				output = 'Invalid input';
			}
		} else {
			output = 'No input';
		}
	}
</script>

<div class="card">
	<h3>
		D. Cyclic Redundancy Check
	</h3>
	<p>Input (7-bit)</p>
	<input type="text" bind:value={cyclicInput}>

	<button on:click={handleClick}>Check</button>

	<div class="output">
		<span class="output-row">
			<p>Output:</p> 
			{#if output}
				<p class="output-tag">{output}</p>
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
