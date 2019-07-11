<script>
  import CardWrapper from "./components/CardWrapper.svelte";
  import Navbar from "./components/Navbar.svelte";
  import Checkout from "./components/Checkout.svelte";

  let nav = "home";

  function navHandler(event) {
    nav = event.detail.option;
  }
</script>

<Navbar on:nav={navHandler} />
{#if nav === 'home'}
  <CardWrapper />
{:else}
  <Checkout />
{/if}
