<script>
  import Dropdown from "./lib/Dropdown.svelte";
  import Camera from "./lib/Camera.svelte"

    let cams = [];

    let options = {
      includeImagesBool: "true",
      includeInactiveBool: "false",
    }

  
  let reqOptions = {method: 'GET', headers: {accept: '*/*', 'X-CSRF-TOKEN': ''}};
  
  let endpoint = "https://mkt-api.gcu.edu/linecam/api/v1/images?includeImages="+options.includeImagesBool+"&includeInactive="+options.includeInactiveBool+"&location=";
  
  async function handleChange(inputLocation) {

    const response = await fetch(endpoint+inputLocation, reqOptions)
    const data = await response.json();
    cams = data;
  }

</script>

<main>
  <h1>GCU Line Cameras</h1>

  <Dropdown on:locationChosen={(loc) => handleChange(loc.detail)}/>

  <br><br>
  
  {#each cams as cam}
    <Camera {cam} />
  {/each}

</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');
  
  :root {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  h1 {
    color: rebeccapurple;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }

</style>
