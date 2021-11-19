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
		max-height: 460px;
	}

    button {
		margin-top: 10px;
		width: 100px;
		color: white;
		background-color: #38B2AC;
	}

	button:hover {
		cursor: pointer;
		background-color: #57d1cb;
	}
</style>