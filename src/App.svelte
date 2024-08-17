<script>
  import { get_random } from './utils.js';

  const boats = [
    "boat",
    "yacht",
    "sailboat",
    "dinghy",
    "tug boat",
    "cruise liner",
    "🚢",
    "motor boat",
    "catamaran",
    "kayak",
    "ship",
    "speed boat",
    "fishing boat",
    "pirate ship",
    "submarine",
    "ferry",
    "houseboat",
    "skiff",
    "canoe",
    "barge",
    "navy cruiser",
    "gondola",
    "lifeboat",
    "water taxi",
    "big boat",
    "small boat",
    "cool boat",
    "fast boat",
    "slow boat"
  ];

  let boat = get_random(boats);

  const update_boat = () => {
    let temp = boat;
    while (temp === boat) {
      temp = get_random(boats);
    };
    boat = temp;
  };

  let exclamations = "";
</script>


<main>
  <h1 class="noselect">i'm a {boat} <strong>•</strong> help{exclamations}</h1>

  <br>

  <div id="ugbuttons" class="noselect">
    <button on:click={update_boat}> Chug </button>
    <button on:click={() => {exclamations = exclamations + "!"}}> Tug </button>
  </div>
</main>

<style>
  #ugbuttons > button {
   margin: 0em 2em; 
  }
</style>
