<script>
    let twoDime = '';
</script>

<div class="card">
    <h3>
        B. Two-dimensional Parity Check
    </h3>
    <p>Input A (45-bit)</p>
    <input type="text" bind:value={twoDime}>

    <button>Check</button>

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
