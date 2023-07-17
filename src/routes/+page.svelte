<script>
import { onMount } from "svelte";
import { preloadCode, preloadData } from '$app/navigation'
import { base } from '$app/paths'

onMount(async () => {
  await preloadCode(`/preload-code-without-base`)
  await preloadCode(`${base}/preload-code-with-base`)
  try {
    await preloadData(`/preload-data-without-base`)
  } catch (e) {
    console.error(e)
  }
  await preloadData(`${base}/preload-data-with-base`)
})
</script>

<h1>
  <code>preloadCode</code> and <code>preloadData</code>
</h1>

<p>Open the console to see which files were preloaded.</p>
