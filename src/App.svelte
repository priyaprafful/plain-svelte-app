<script>
	import Client from './client'
	import  * as PrismicHelpers from "@prismicio/helpers";

	async function getResponse() {
	  let response = await Client().getSingle('blog_homepage');
	  console.log (response)
	  return response
	  
   }
   const response = getResponse()
</script>

<h1>Basic Plain Svelte App</h1>

{#if response===undefined}
 <p>Response is undefined</p>
{:else}
{#await response}
  <p>Loading...</p>
{:then results}
  { PrismicHelpers.asText(results.data.main_title)}
{:catch error}
  <p>Something went wrong:</p>
<pre>{error.message}</pre>
{/await}
{/if}