<script>
  import "../../app.css";
  import "../../project_page.css";
  import { Router } from "svelte-routing";
  import { setContext } from "svelte";
  import { writable } from "svelte/store";

  export let url = "";
  const currentProject = writable(null);
  setContext("currentProject", currentProject);
</script>

<Router {url}>
  <slot />
</Router>
