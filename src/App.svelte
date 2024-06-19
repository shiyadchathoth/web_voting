<script>
    let selectedCandidate = '';
    let voteSubmitted = false;

    const candidates = ['shiyad', 'shiyas', 'Charlie'];

    function submitVote() {
        voteSubmitted = true;
    }

    function resetForm() {
        selectedCandidate = '';
        voteSubmitted = false;
    }
</script>

<style>
    .container {
        background: white;
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
        width: 300px;
        text-align: center;
        margin: 0 auto;
        margin-top: 50px;
    }

    h1, h2 {
        color: #333;
    }

    label {
        font-size: 1.2em;
    }

    button {
        background-color: #007BFF;
        color: white;
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }

    button:hover {
        background-color: #0056b3;
    }

    #result {
        margin-top: 20px;
        font-size: 1.2em;
        color: green;
    }
</style>

<div class="container">
    <h1>School Voting System</h1>
    {#if !voteSubmitted}
        <form on:submit|preventDefault={submitVote}>
            <h2>Vote for Class President</h2>
            {#each candidates as candidate}
                <label>
                    <input type="radio" name="candidate" bind:group={selectedCandidate} value={candidate} required>
                    {candidate}
                </label><br>
            {/each}
            <button type="submit">Submit Vote</button>
        </form>
    {:else}
        <div id="result">
            You voted for: {selectedCandidate}
        </div>
        <button on:click={resetForm}>Vote Again</button>
    {/if}
</div>
