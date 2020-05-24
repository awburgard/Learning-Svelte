<script>
  let result = "";
  let correctAnswer = "b"
  let totalIncome = 0

  function pickAnswer(answer) {
    if (answer === correctAnswer) {
      return (result = 'Correct!')
    }
    result = 'DOH!'
  }

  function calculateTotalIncome (income){
    let thirtyPercent = 0.3
    return (totalIncome = totalIncome * thirtyPercent)
  }
</script>

<div>
  <h4>{result}</h4>
  <button on:click on:click={() => pickAnswer('a')}>Answer A</button>
  <button on:click on:click={() => pickAnswer('b')}>Answer B</button>
  <button on:click on:click={() => pickAnswer('c')}>Answer C</button>
  <button on:click on:click={() => pickAnswer('d')}>Answer D</button>
  <input bind:value={totalIncome} type="number" />
  <button on:click={() => calculateTotalIncome(totalIncome)}>Submit</button>
  <h4>{totalIncome}</h4>
</div>
