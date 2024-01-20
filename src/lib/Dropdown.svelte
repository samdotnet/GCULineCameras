<script>

  import { createEventDispatcher } from "svelte"
  const dispatch = createEventDispatcher()

  let location = "Select"
  
</script>

<form method="POST">
  <label for="locationSelect">Choose a location:</label>
  <select name="location" id="location" bind:value={location} on:change={() => dispatch('locationChosen', location)}>
    <option value="31st Ave. Parking Garage">Mail Center</option>
    <option value="Aqua Fria Apartments (76)">Agua Fria Apts</option>
    <option value="Camelback Hall (37)">Camelback Hall</option>
    <option value="Chaparral Hall (45)">Chaparral Hall</option>
    <option value="Diamondback Apartments (50)">Diamondback Apts</option>
    <option value="GCU Arena (38)">GCU Arena</option>
    <option value="Juniper Hall (84)">Juniper Lopes Mart</option>
    <option value="Prescott Hall (36)">Prescott Hall</option>
    <option value="Roadrunner Appartments (28)">Roadrunner GCBC</option>
    <option value="Student Union (29)">Student Union</option>
    <option value="Technology Building (57)">Esports Lounge</option>
    <option value="Thunderground (11)">Thunderground</option>
    <option value="Turquoise Apartments (61)">Turquoise Purple Greens</option>
    <option value="Verde River Apartments (78)">Verde River Apts</option>
  </select>
</form>