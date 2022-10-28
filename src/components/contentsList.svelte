<script>
  export let headings;
  let el;
  function toggleList() {
    el.classList.toggle("visible");
  }
</script>

<aside class="visible" bind:this={el}>
  <button class="toggle" on:click={toggleList}>Outline</button>
  <h4>Contents</h4>
  {#each headings as heading}
    <a href={"#" + heading.slug}>{heading.text}</a>
  {/each}
</aside>
