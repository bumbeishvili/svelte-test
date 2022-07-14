<script>
 import Modal from "./Modal.svelte";
 import AddPersonForm from "./AddPersonForm.svelte";

 let people = [
  {name: "yoshi", beltColor: "black", age: 25, id: 1},
  {name: "mario", beltColor: "orange", age: 45, id: 2},
  {name: "luigi", beltColor: "brown", age: 35, id: 3},
 ];
 const handleClick = (person) => {
  people = people.filter((d) => d != person);
 };

 let showModal = true;
 let isPromo = true;

 const toggleModal = () => {
  showModal = !showModal;
 };

 const addPerson = (e) => {
    const person = e.detail;
    people = [...people, person];
    showModal = false;
 };
</script>

<Modal {isPromo} {showModal} on:click={toggleModal}>
 <AddPersonForm on:addPerson={addPerson} />
</Modal>

<main>
 <button on:click={toggleModal}> Open Modal </button>
 {#each people as person (person.id)}
  <div>
   <h4>{person.name}</h4>
   {#if person.beltColor === "black"}
    <p><strong>master ninja</strong></p>
   {/if}
   <p>{person.age} years old {person.beltColor} belt</p>
   <button on:click={(event) => handleClick(person)}> delete</button>
  </div>
 {:else}
  <p>No people</p>
 {/each}
</main>

<style>
 main {
  text-align: center;
  padding: 1em;
  max-width: 240px;
  margin: 0 auto;
 }

 h1 {
  color: #ff3e00;
  text-transform: uppercase;
  font-size: 4em;
  font-weight: 100;
 }

 @media (min-width: 640px) {
  main {
   max-width: none;
  }
 }
</style>
