<script>
 import {createEventDispatcher} from "svelte";
 let dispatch = createEventDispatcher();
 let name;
 let beltColor;
 let age;
 let skills = [];
 //  let fighting = false;
 //  let sneaking = false;
 //  let running = false;

 const handleSubmit = () => {
  const person = {
   id: crypto.randomUUID(),
   name,
   beltColor,
   age,
   skills,
  };
  dispatch("addPerson", person);
 };
</script>

<form on:submit|preventDefault={handleSubmit}>
 <input type="text" bind:value={name} placeholder="name" />
 <input type="text" bind:value={beltColor} placeholder="belt color" />
 <input type="number" bind:value={age} placeholder="age" />
 <label>Skills:</label>
 <input type="checkbox" bind:group={skills} value={"fighting"} />fighting<br />
 <input type="checkbox" bind:group={skills} value={"sneaking"} />sneaking<br />
 <input type="checkbox" bind:group={skills} value={"running"} />running<br />
 <label>Belt color:</label>
 <select bind:value={beltColor}>
  <option value="black">black</option>
  <option value="orange">orange</option>
  <option value="brown">brown</option>
  <option value="white">white</option>
 </select>
 <button>Add Person</button>
</form>

<style>
</style>
