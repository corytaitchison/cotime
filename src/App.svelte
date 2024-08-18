<script>
  const subtractdate = (date, x) => { 
    var newdate = new Date(date);
    newdate.setTime(newdate.getTime() - x*1000);
    return newdate
  }
  const daysInThisMonth = () => {
    var now = new Date();
    return new Date(now.getFullYear(), now.getMonth()+1, 0).getDate();
  }
  const printtime = (date) => date.toLocaleTimeString("en-US");

  const offset = () => {
    var monthday = now.getDate();
    var monthtotal = daysInThisMonth(); 
    var dayfrac = (now.getHours() * 60 * 60 + now.getMinutes() * 60 +
      now.getSeconds()) / (24 * 60 * 60);
    var monthfrac = (monthday - 1 + dayfrac) / monthtotal; 
    return monthfrac * 60 * 60;
  }

  let now;
  const updateTime = () => {
    now = new Date(); 
  }
  updateTime();
  setInterval(updateTime, 1000);

  let state = { truetime: false, difference: false };

</script>

<main class="noselect">
  <div class={"clock " + (state.truetime ? "truetime" : "cotime")}>
    <h1 class="noselect"> <strong >
      {printtime(state.truetime ? now :
      subtractdate(now, offset()))}</strong> 
    </h1>
  </div>
  <h2 class="noselect" style={state.difference ? " " :
    "color: var(--main-bg-color)"}> 
    True Time is {Math.round(offset() / 60 * 10)/10} minutes ahead.
  </h2>
  <button class={"noselect " + (state.truetime ? "active" : " ")}
    on:click={() => state.truetime = !state.truetime}>
    {#if state.truetime}
      Hide
    {:else}
      Show
    {/if}
    True Time
  </button> 
  <button class="noselect" on:click={() => state.difference =
    !state.difference}> Toggle Difference </button>
</main>

<style>
</style>
