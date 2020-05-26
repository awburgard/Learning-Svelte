<script>
  let result = null;
  let correctAnswer = "b";
  let answers = ["a", "b", "c", "d"];

  function pickAnswer(answer) {
    if (answer === correctAnswer) {
      return (result = "Correct!");
    }
    result = "DOH!";
  }
</script>

<style>
  h4 {
    color: red;
  }
</style>

<div>
  {#if result}
    <h4>{result}</h4>
  {:else}
    <h5>Please choose an answer</h5>
  {/if}
  {#each answers as answer}
    <button on:click={() => pickAnswer(answer)}>
      Answer {answer.toUpperCase()}
    </button>
  {/each}
</div>
