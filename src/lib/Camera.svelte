<script>
    
  import { onMount } from "svelte";
  import { DateTime } from "luxon";
  
  export let cam = {
    url: "url",
    description: "description"
  }
  
</script>

<div>
  <img src={cam.url} alt="Camera View">
  <p>Description: {cam.description}</p>
  <p>Last updated: {DateTime.fromISO(cam.updated_at).toRelative()} at {DateTime.fromISO(cam.updated_at).toLocaleString(DateTime.DATETIME_SHORT)}</p>
</div>

<style>
  img {
    height: 16rem;
  }
</style>