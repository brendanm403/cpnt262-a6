<script>
  import Button from "$lib/components/Button.svelte";
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
  // makes a new object based on an existing object //
  // let inputObj = Object.create(objArr[0]);
  // inputObj.fName = "carl"
  // console.log(inputObj);

  const displayUserInput = function() {
    // make a new object with existing object as prototype //
    let newChar = Object.create(objArr[0]);
    // set the values for each key //
    newChar.fName =  firstName;
    newChar.lName = lastName;
    newChar.house = house;
    console.log(newChar);
    // reassign array to trigger reactivity //
    objArr = [...objArr, newChar];
  }

  // store the value entered in first name input in global variable //
  const getFirstName = function(event) {
    firstName = event.target.value; 
  }

  // store the value entered in last name input in global variable //
  const getLastName = function(event) {
    lastName = event.target.value; 
  }

  // store the value entered in house input in global variable //
  const getHouse = function(event) {
    house = event.target.value; 
  }

  // clears input field when clicked on //
  const resetInput = function(event) {
    event.target.value = "";
  }

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
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="fName" on:change={getFirstName} on:focus={resetInput}>
<label class="mt-5 w-56 mx-auto block text-center" for="lName">Character Last Name</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="lName" on:change={getLastName} on:focus={resetInput}>
<label class="mt-5 w-56 mx-auto block text-center" for="house">Character House</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="house" on:change={getHouse} on:focus={resetInput}>
<Button on:handleClick={displayUserInput} buttonText="Add Character"/>
<Button buttonText="Toggle" on:handleClick={toggle}/>

<style>
  :global(body.dark-mode) {
    background-color: #000;
    color: aliceblue;
  }
</style>