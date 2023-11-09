<script>
  let objArr = [
    {fName: "Tom", lName: "Riddle", house: "Slytherin"},
    {fName: "Harry", lName: "Potter", house: "Gryffindor"},
    {fName: "Hermione", lName: "Granger", house: "Gryffindor"},
    {fName: "Cedric", lName: "Diggory", house: "Ravenclaw"},
    {fName: "Draco", lName: "Malfoy", house: "Slytherin"}, 
  ]
  let inputObj = {};
  console.log(objArr);
</script>

<main class="flex flex-wrap justify-center gap-10 p-5">
  {#each objArr as character}
    <div>
      <h2 class="text-2xl mb-3">{character.fName} {character.lName}</h2>
      <p class="text-center">{character.house}</p>
    </div>
  {/each}
</main>

<label class="mt-12 w-56 mx-auto block text-center" for="fName">Character First Name</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="fName">
<label class="mt-5 w-56 mx-auto block text-center" for="lName">Character Last Name</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="lName">
<label class="mt-5 w-56 mx-auto block text-center" for="house">Character House</label>
<input class="block bg-black text-green-200 border-2 rounded-lg border-green-400 mx-auto" type="text" id="house">