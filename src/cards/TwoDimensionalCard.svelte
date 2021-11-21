<script>
    let twoDime = '';
	let output = '';

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

	function toArray(data) {
		let arr = new Array(5);

		for (let i = 0; i < arr.length; i++) {
			arr[i] = new Array(9);
		}

		for (let i = 0; i < 5; i++) {
			for (let j = 0; j < 9; j++) {
				arr[i][j] = data[((i*9)+(j+1))-1];
			}
		}
		return arr;
	}

	function getColParity(data) {
		let errorCount = 0;
		let column = [];

		for (let j = 0; j < 9; j++) {
			for (var i = 0; i < 4; i++) {
				column.push(data[i][j])
			}
			
			let	parityBit = generateParity(column);

			if(parityBit!==(data[i][j])) {
				errorCount++;
			}
			column = [];
		} 
		return errorCount;
	}

	function getRowParity(data) {
		let errorCount = 0;
		let row = [];

		for (let i = 0; i < 4; i++) {
			for (var j = 0; j < 8; j++) {
				row.push(data[i][j])
			}
			
			let	parityBit = generateParity(row);

			if(parityBit!==(data[i][j])) {
				errorCount++;
			}
			row = [];
		} 
		return errorCount;
	}

	function handleClick() {
		if (twoDime) {
			let data = twoDime.replace(/\s/g,'');
			let isValidInput = data.length === 45 && isValidBinary(data);

			if (isValidInput) {
				data = toArray(data);
				
				let colParity = getColParity(data);
				let rowParity = getRowParity(data);

				output = colParity + rowParity;

				if (output === 0) {
					output = '0';
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
        B. Two-dimensional Parity Check
    </h3>
    <p>Input (45-bit)</p>
    <input type="text" bind:value={twoDime}>

	<button on:click={handleClick}>Check</button>

	<div class="output">
		<span class="output-row">
			<p>Error Count:</p> 
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
