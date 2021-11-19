<script>
    let simpleParityA = '';
	let simpleParityB = '';
</script>

<div class="card">
    <h3>
        A. Simple Parity Check (Even Parity)
    </h3>
    <p>Data Word (8-bit)</p>
    <input type="text" bind:value={simpleParityA}>

    <p>Code Word (8-bit and Parity bit)</p>
    <input type="text" bind:value={simpleParityB}>

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