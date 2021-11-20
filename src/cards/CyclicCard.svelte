<script>
    let cyclicInput = '';
</script>

<div class="card">
	<h3>
		D. Cyclic Redundancy Check
	</h3>
	<p>Input A (7-bit)</p>
	<input type="text" bind:value={cyclicInput}>

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
		height: 420px;
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
