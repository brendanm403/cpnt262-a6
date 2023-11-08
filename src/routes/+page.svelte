<script>
  const objArr = [
    {fName: "Tom", lName: "Riddle", house: "Slytherin"},
    {fName: "Harry", lName: "Potter", house: "Gryffindor"},
    {fName: "Hermione", lName: "Granger", house: "Gryffindor"},
    {fName: "Cedric", lName: "Diggory", house: "Ravenclaw"},
    {fName: "Draco", lName: "Malfoy", house: "Slytherin"}, 
  ]
</script>

<main class="flex flex-wrap justify-center gap-10 p-5">
  {#each objArr as character}
    <div>
      <h2 class="text-2xl mb-3">{character.fName} {character.lName}</h2>
      <p class="text-center">{character.house}</p>
    </div>
  {/each}
</main>

