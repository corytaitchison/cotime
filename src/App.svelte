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

  let monthday;
  let monthtotal;
  const offset = () => {
    monthday = now.getDate();
    monthtotal = daysInThisMonth(); 
    var monthfrac = monthday / monthtotal; 
    return monthfrac * 60 * 60;
  }

  let now;
  const updateTime = () => {
    now = new Date(); 
  }
  updateTime();
  setInterval(updateTime, 1000);

</script>

<main>
  <h1 class="noselect"> Cotime is <strong>{printtime(subtractdate(now,
    offset()))}</strong>. </h1>
  <h2 class="noselect"> (Day {monthday} out of {monthtotal}) </h2>
  <h2 class="noselect"> Actual time is {printtime(now)}. You are {Math.round(offset()
  / 60 * 100)/100} minutes behind.</h2>
</main>

<style>
</style>
