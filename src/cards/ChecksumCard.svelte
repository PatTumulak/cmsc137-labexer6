<script>
    let checksumInput = '';
	let output = '';

	function isValidBinary(input) {
		for (let i of input) {
			if (i !== '0'&& i != '1') {
				return false;
			}
		}
		return true;
	}

	// from tutorialspoint
	function addBinary(str1, str2) {
		let carry = 0;
		const res = [];
		let l1 = str1.length, l2 = str2.length;
		for (let i = l1 - 1, j = l2 - 1; 0 <= i || 0 <= j; --i, --j) {
			let a = 0 <= i ? Number(str1[i]) : 0,
			b = 0 <= j ? Number(str2[j]) : 0;
			res.push((a + b + carry) % 2);
			carry = 1 < a + b + carry;
		};
		if (carry){
			res.push(1);
		}
		return res.reverse().join('');
	};

	function separateWords(input) {
		let packets = [];

		for (let i = 0; i < 5; i++) {
			packets.push(input.substring(i*8, (i*8)+8));
		}
		console.log(packets)
		return packets
	}

	function addPackets(packets) {
		let tempSum = '';
		let currSum = packets[0];

		for (let i = 1; i < 5; i++) {
			tempSum = addBinary(currSum, packets[i]);
			
			if (tempSum.length === 9) {
				currSum = addBinary(tempSum.substring(1), '1');
			} else {
				currSum = tempSum;
			}
		}
		return currSum;
	}

	function onesComplement(input) {
		let onesComplement = '';
		
		for (let i = 0; i < input.length; i++) {
			onesComplement += input[i] === '0' ? '1' : '0';
		}

		return onesComplement;
	}

	function handleClick() {
		if (checksumInput) {
			let data = checksumInput.replace(/\s/g,'');
			let isInputValid = data.length === 40 && isValidBinary(data);

			if (isInputValid) {
				let packets = separateWords(data);
				packets = addPackets(packets);
				packets = onesComplement(packets);

				if (packets === '00000000') {
					output = 'Accept Data';
				} else {
					output = 'Checksum error detected';
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
		C. Checksum
	</h3>
	<p>Input (40-bit)</p>
	<input type="text" bind:value={checksumInput}>

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
