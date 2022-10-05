<script>
  import { onMount } from "svelte";
  export let selector;

  let headerRef;
  function throttle(fn, wait) {
    var time = Date.now();
    return function () {
      if (time + wait - Date.now() < 0) {
        fn();
        time = Date.now();
      }
    };
  }
  onMount(() => {
    const elementToScrollBy = document.querySelector(selector);
    document.addEventListener(
      "scroll",
      throttle((e) => {
        if (document.documentElement.scrollTop > elementToScrollBy.clientHeight) {
          headerRef.classList = "visible";
        } else {
          headerRef.classList = "";
        }
      }, 100)
    );
  });
</script>

<header bind:this={headerRef}>lol</header>
