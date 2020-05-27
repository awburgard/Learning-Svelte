<script>
  export let question;

  let isCorrect;
  let isAnswered = false;

  let answers = question.incorrect_answers.map(answer => {
    return {
      answer,
      correct: false
    };
  });

  let allAnswerrs = [
    ...answers,
    {
      answer: question.correct_answer,
      correct: true
    }
  ];

  shuffle(allAnswerrs);

  function shuffle(array) {
    array.sort(() => Math.random() - 0.5);
  }

  function checkQuestion(correct) {
    isAnswered = true;
    isCorrect = correct;
  }
</script>

<h3>
  {@html question.question}
</h3>

{#if isAnswered}
  <h4>
    {#if isCorrect}You got it right!{:else}You done goofed!{/if}
  </h4>
{/if}

{#each allAnswerrs as answer}
  <button on:click={() => checkQuestion(answer.correct)}>
    {@html answer.answer}
  </button>
{/each}
