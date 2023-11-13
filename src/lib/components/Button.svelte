<script>
  import {createEventDispatcher} from "svelte";
  const dispatch = createEventDispatcher();
  // function dispatch //
  const defaultFn = function() {
    dispatch("handleClick", {})
  }
  export let buttonText = "button text"
</script>

<button class="block mt-5 bg-purple-600 p-2 text-white text-xs rounded-2xl hover:bg-purple-700 mx-auto active:bg-purple-900 active:text-white active:scale-90" on:click={defaultFn}>{buttonText}</button>