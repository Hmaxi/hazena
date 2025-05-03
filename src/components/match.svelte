<script>
  import { timer, time, isRunning, isComplete } from "../stores/countdown-timer";
  import { Button } from "wx-svelte-core";

  const goalList = $state([]);

  let lastTime = 0
  let goalsPrichovice = $state(0)
  let goalsSouper = $state(0)
  let {name} = $props();

  time.subscribe((value) => {lastTime = value})
  timer.start()
  
  function golPrichovice() {
    goalList.push({time: lastTime, team: 'Prichovice'})
    goalsPrichovice++
  }

  function golSouper() {
    goalList.push({time: lastTime, team: name})
    goalsSouper++
  }

</script>


<h2>Prichovice x {name}</h2>
<h2>{goalsPrichovice} x {goalsSouper}</h2>
<div class="countdown">{$time}</div>
<br>
<Button type={"primary"} onclick={golPrichovice}>Gol Prichovice</Button>
<Button type={"primary"} onclick={golSouper}>Gol {name}</Button>
<br><br>
<section>
  {#each goalList as gol}
    <article>{gol.time} - {gol.team}</article>
  {/each}
</section>

<style>
  .countdown {
    font-size: large;
  }
</style>