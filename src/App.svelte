<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate, tick } from 'svelte';
  let photos = [];
  onMount(async () => {
    const res = await fetch(`https://jsonplaceholder.typicode.com/photos?_limit=20`);
    photos = await res.json();
  }) 

export function onInterval(callback, milliseconds) {
  const interval = setInterval(callback, milliseconds);
  onDestroy(() => {
    clearInterval(interval);
  });
}

let div;
let autoscroll;
beforeUpdate(() => {
  autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
})
afterUpdate(() => {
  if(autoscroll) div.scrollTo(0, div.scrollHeight);
})

await tick();
</script>

<main>
  <h3>App component global style</h3>
</main>

<style>
  :global(h3){
    color: blue;
  }
  h4{
    color: orange;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
