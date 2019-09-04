<script>
import { scale } from "svelte/transition";
export let quote;
export let scaling
</script>


{#if quote}
    <div class="container" transition:scale>
        <p id="text" >{quote.quote}</p>
        <p id="author" >{quote.author}</p>
    </div >
    {:else}
        <p>loading</p>
{/if}