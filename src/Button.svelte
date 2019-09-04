<script>
        import { createEventDispatcher } from "svelte";

        export let href;
        export let quote;
        export let id;
        export let color;

        const dispatch = createEventDispatcher();

        function twit() {
          dispatch("twit", "");
        }

        function newQuote() {
          dispatch("newQ", "");
        }
</script>

<style>
  button,
  a {
    /* background-color:#008CBA; */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 10px;
  }
  #tweet-quote {
    background-color: #008cba;
  }
  #new-quote {
    background-color: #f44336;
  }
</style>

{#if href}
    <a {id} target="_blank" {href} ><slot/></a>
{:else }
    <button {id} on:click={newQuote}><slot/></button>
{/if} 
