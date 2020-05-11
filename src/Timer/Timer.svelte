<script>
  import ProgressBar from "./../ProgressBar/ProgressBar.svelte";
</script>

<style>
  h2 {
    margin: 0;
  }
  .start {
    background-color: rgb(41, 185, 149);
    width: 100%;
    margin: 10px 0;
  }
</style>

<div bp="grid">
  <h3 bp="offset-5@md 4@md 12@sm">Seconds Left:</h3>
</div>
<ProgressBar />
<button class="start">Start</button>
