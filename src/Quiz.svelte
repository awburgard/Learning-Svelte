<script>
  import { fade, blur, fly, slide, scale } from "svelte/transition";
  import Question from "./Question.svelte";
  import Modal from "./Modal.svelte";
  let activeQuestion = 0;
  import { score } from "./store.js";
  let quiz = getQuiz();
  let isModalOpen = false;

  async function getQuiz() {
    const res = await fetch(
      "https://opentdb.com/api.php?amount=10&category=21&type=multiple"
    );
    const quiz = await res.json();
    return quiz;
  }

  function nextQuestion() {
    activeQuestion = activeQuestion + 1;
  }

  function resetQuiz() {
    isModalOpen = false;
    score.set(0);
    activeQuestion = 0;
    quiz = getQuiz();
  }

  // Reactive Statement
  $: if ($score > 0) {
    isModalOpen = true;
  }

  // Reactive Declaration
  $: questionNumber = activeQuestion + 1;
</script>

<div>
  <button on:click={resetQuiz}>Start New Quiz</button>

  <h3>My Score: {$score}</h3>
  <h4>Question #{questionNumber}</h4>

  {#await quiz}
    Loading....
  {:then data}

    {#each data.results as question, index}
      {#if index === activeQuestion}
        <div in:fade={{ delay: 200 }} out:fade={{ duration: 200 }}>
          <Question {nextQuestion} {question} />
        </div>
      {/if}
    {/each}

  {/await}
</div>

{#if isModalOpen}
  <Modal on:close={resetQuiz}>
    <h2>You won!</h2>
    <p>Congrats!</p>
    <button on:click={resetQuiz}>Start Over</button>
  </Modal>
{/if}
