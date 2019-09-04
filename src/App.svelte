<script>
 import { onMount, tick } from "svelte";
 import Quote from "./Quote.svelte";
 import Button from "./Button.svelte";

 let quotes = "";
 let quote = "";

 

 onMount(async () => {
   const res = await fetch(
     'https://gist.githubusercontent.com/camperbot/5a022b72e96c4c9585c32bf6a75f62d9/raw/e3c6895ce42069f0ee7e991229064f167fe8ccdc/quotes.json'
   );
   let data = await res.json();
   quotes=data.quotes
   let r = Math.floor(Math.random() * quotes.length);
   quote = quotes[r]
 });

 function handleClick() {
   quote = "";
   setTimeout(() => {
     quote = quotes[Math.floor(Math.random() * quotes.length)];
   },1000);
 }
</script>

<style>
  #quote-box {
    margin: 50px auto;
    width: 50%;
    border: 3px solid green;
    padding: 10px;
    text-align: center;
    background: whitesmoke;
  }
</style>


<div id="quote-box">
<Quote {quote} />


<Button on:newQ={handleClick}
id="new-quote">New Quote</Button>

<Button 
href="{`https://twitter.com/intent/tweet?text="${quote.quote}"-${quote.author}`}" 
{quote} id="tweet-quote">
Twit</Button>

</div>