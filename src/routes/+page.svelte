<script>
  import Button from "$lib/components/Button.svelte";
	import Card from "../lib/Card.svelte";
  let objArr = [
    {fName: "Tom", lName: "Riddle", house: "Slytherin"},
    {fName: "Harry", lName: "Potter", house: "Gryffindor"},
    {fName: "Hermione", lName: "Granger", house: "Gryffindor"},
    {fName: "Cedric", lName: "Diggory", house: "Ravenclaw"},
    {fName: "Draco", lName: "Malfoy", house: "Slytherin"}, 
  ]
  
  let firstName;
  let lastName;
  let house;

  let cardHeading = "Slytherin"
  
  const displayUserInput = function() {
    // prevent user from submitting undefined values //
    if (typeof firstName === "undefined" || typeof lastName === "undefined" || typeof house === "undefined") {
      alert("Fields must not be left empty!"); 
    } else {
      // make a new object with existing object as prototype //
      let newChar = Object.create(objArr[0]);
      // set the values for each key //
      newChar.fName = firstName;
      newChar.lName = lastName;
      newChar.house = house;
      console.log(newChar);
      // reassign array to trigger reactivity //
      objArr = [...objArr, newChar];
    }
  }

  // gets the user input and stores it in a variable depending on which input is fires the event //
  const getInputValues = function(event) {
    if (event.target.id === "fName") {
      firstName = event.target.value;
    } else if (event.target.id === "lName") {
      lastName = event.target.value;
    } else {
      house = event.target.value;
    }
  }

  // clears input field when clicked on, reset variable to undefined so user must type in new value //
  const resetInput = function(event) {
    event.target.value = "";
    if (event.target.id === "fName") {
      firstName = undefined;
    } else if (event.target.id === "lName") {
      lastName = undefined;
    } else {
      house = undefined;
    }
  }

  // function to toggle between light and dark mode, passed to toggle button //
  const toggle = function() {
    window.document.body.classList.toggle("dark-mode");
  }
</script>

<main class="flex flex-wrap justify-center gap-10 p-5">
  <!-- loop through array to render object values on screen -->
  {#each objArr as character}
    <div>
      <h2 class="text-2xl mb-3">{character.fName} {character.lName}</h2>
      <p class="text-center">{character.house}</p>
    </div>
  {/each}
</main>

<label class="mt-12 w-56 mx-auto block text-center" for="fName">Character First Name</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="fName" on:change={getInputValues} on:focus={resetInput}>
<label class="mt-5 w-56 mx-auto block text-center" for="lName">Character Last Name</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="lName" on:change={getInputValues} on:focus={resetInput}>
<label class="mt-5 w-56 mx-auto block text-center" for="house">Character House</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="house" on:change={getInputValues} on:focus={resetInput}>
<Button on:handleClick={displayUserInput} buttonText="Add Character"/>
<Button buttonText="Toggle" on:handleClick={toggle}/>

<!-- I had to put this together super quick because I thought step 4 was removed but then I saw it appeared again in the instructions, hopefully this is somewhat what you were looking for for that step. -->
<Card />

<!--  styles for dark mode  -->
<style>
  :global(body) {
    transition: background-color 0.5s;
  }
  :global(body.dark-mode) {
    background-color: #000;
    color: aliceblue;
  }
</style>