<script>
  import {createEventDispatcher} from "svelte";
  const dispatch = createEventDispatcher();
  // function dispatch //
  const defaultFn = function() {
    dispatch("renderCharacter", {})
  }
  export let buttonText = "button text"
</script>

<button class="block mt-5 bg-purple-400 p-2 text-xs rounded-2xl hover:bg-purple-600 mx-auto active:bg-purple-900 active:text-white active:scale-90" on:click={defaultFn}>{buttonText}</button>