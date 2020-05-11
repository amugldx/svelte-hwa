<script>
  import { createEventDispatcher } from "svelte";
  import ProgressBar from "./../ProgressBar/ProgressBar.svelte";

  const totalSeconds = 20;
  let secondsLeft = totalSeconds;
  let isRunning = false;

  $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100;

  const dispatch = createEventDispatcher();

  const startTimer = () => {
    isRunning = true;
    const timer = setInterval(() => {
      secondsLeft -= 1;
      if (secondsLeft === 0) {
        clearInterval(timer);
        isRunning = false;
        secondsLeft = totalSeconds;
        dispatch("end");
      }
    }, 1000);
  };
</script>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(46, 120, 204);
    color: white;
    width: 100%;
    margin: 10px 0;
  }
  .start[disabled] {
    background: rgb(194, 194, 194);
    cursor: not-allowed;
    color: black;
  }
</style>

<div bp="grid">
  <h3 bp="offset-5@md 4@md 12@sm">Seconds Left: {secondsLeft}</h3>
</div>
<ProgressBar {progress} />
<div bp="grid">
  <button
    disabled={isRunning}
    on:click={startTimer}
    bp="offset-5@md 4@md 12@sm"
    class="start">
    Start
  </button>
</div>
