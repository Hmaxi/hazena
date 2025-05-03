<script>
  import { timer, time, isRunning, isComplete } from "../stores/countdown-timer";

  const goalList = $state([]);

  let lastTime = 0
  let goalsPrichovice = $state(0)
  let goalsSouper = $state(0)

  time.subscribe((value) => {lastTime = value})
  
  function golPrichovice() {
    goalList.push({time: lastTime, team: 'Prichovice'})
    goalsPrichovice++
  }

  function golSouper() {
    goalList.push({time: lastTime, team: 'Souper'})
    goalsSouper++
  }

</script>


<h2>Prichovice x souper</h2>
<h2>{goalsPrichovice} x {goalsSouper}</h2>
<div class="countdown">{$time}</div>
  <div class="buttons">
    {#if !$isComplete}
      {#if $isRunning}
        <button onclick={() => timer.pause()}>pause</button>
      {:else}
        <button onclick={() => timer.start()}>start</button>
      {/if}
    {/if}
  </div>
<br>
<button onclick={golPrichovice}>Gol Prichovice</button>
<button onclick={golSouper}>Gol Souper</button>
<br>
<section>
  {#each goalList as gol}
    <article>{gol.time} - {gol.team}</article>
  {/each}
</section>