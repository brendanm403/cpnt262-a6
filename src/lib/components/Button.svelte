<script>
  import {createEventDispatcher} from "svelte";
  const dispatch = createEventDispatcher();
  // function dispatch //
  const defaultFn = function() {
    dispatch("getUserInput", {})
  }
</script>

<button class="block my-1 bg-purple-400 p-2 text-xs rounded-2xl hover:bg-purple-600 mx-auto active:bg-purple-900 active:text-white active:scale-90" on:click={defaultFn}>Submit</button>