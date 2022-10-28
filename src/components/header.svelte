<script>
  import { onMount } from "svelte";
  export let selector;
  export let currentPage = undefined;

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

<header bind:this={headerRef}>
  <a id="nav-home" href="/trainzzz/"><img src="/logo.png" alt="T4E" /></a>
  <nav>
    <a href="/trainzzz/about">Our Mission</a>
    <a href="/trainzzz/team">Meet The Team</a>
    <a href="/trainzzz/contact">Contact Us</a>
    <a href="/trainzzz/world">World Guide</a>
  </nav>
</header>
