<script>
  let result = null;
  let correctAnswer = "b";

  function pickAnswer(answer) {
    if (answer === correctAnswer) {
      return (result = "Correct!");
    }
    result = "DOH!";
  }
</script>

<div>
  {#if result}
    <h4>{result}</h4>
  {:else}
  <h5>Please choose an answer</h5>
  {/if}
  <button on:click on:click={() => pickAnswer('a')}>Answer A</button>
  <button on:click on:click={() => pickAnswer('b')}>Answer B</button>
  <button on:click on:click={() => pickAnswer('c')}>Answer C</button>
  <button on:click on:click={() => pickAnswer('d')}>Answer D</button>
</div>
