<script>
  import Button from "$lib/components/Button.svelte"

  export let heading = "Is This Gryffindor?"
  export let cardColor = "bg-red-600"

  const changeCard = function() {
    heading = "No! It's Slytherin!"
    cardColor = "bg-green-600";
  }
  
</script>

<article class="{cardColor} p-2 rounded-lg max-w-fit mx-auto my-5">
  <img class="block w-32 mx-auto" src="/images/slytherin-crest.webp" alt="a house crest">
  <h2 class="text-center my-2">{heading}</h2>
  <p class="w-56 text-center">Click the button to for the answer!</p>
  <Button on:handleClick|once = {changeCard} buttonText="Revelio"/>
</article>


