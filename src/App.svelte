<script>
  import HowTo from "./HowTo/HowTo.svelte";
  import Timer from "./Timer/Timer.svelte";

  let audio;
  const timerEnds = () => {
    audio.play();
  };
</script>

<style>
  h1 {
    text-align: center;
  }
</style>

<h1>Handwashing App</h1>
<Timer on:end={timerEnds} />
<HowTo />

<audio bind:this={audio}>
  <source src="sound.wav" />
</audio>
