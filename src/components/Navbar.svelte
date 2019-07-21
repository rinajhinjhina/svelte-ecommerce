<script>
  import { cart } from "../stores/stores.js";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let cart_sum = 0;

  const unsubscribe = cart.subscribe(items => {
    const itemValues = Object.values(items);
    cart_sum = 0;
    itemValues.forEach(item => {
      cart_sum += item.count;
    });
  });

  function goToHome() {
    dispatch("nav", {
      option: "home"
    });
  }

  function goToCheckout() {
    dispatch("nav", {
      option: "checkout"
    });
  }
</script>

<style>
  header {
    width: 100vw;
    position: fixed;
    top: 0;
    background: #20447d;
    color: white;
  }

  ul > li:first-child {
    font-family: "Molengo", sans-serif;
  }

  ul {
    list-style-type: none;
    width: 70vw;
    min-height: 50px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-left: 0;
  }

  ul li {
    align-self: center;
    height: 100%;
    cursor: pointer;
  }

  ul li:last-child {
    position: relative;
    display: flex;
    align-items: center;
  }

  ul li .shopping-cart {
    margin-left: 0.5em;
  }

  ul li .circle {
    position: absolute;
    top: -2px;
    right: -5px;
    background-color: #fffd85;
    color: #000;
    font-weight: 700;
    padding: 0.1em;
    text-align: center;
    line-height: 1em;
    font-size: 0.6em;
    width: 1em;
    height: 1em;
    border-radius: 1em;
    box-shadow: 0 0 1px rgba(0, 0, 0, 0.4);
  }

  @media screen and (max-width: 1600px) {
    ul {
      width: 80vw;
    }
  }

  @media screen and (max-width: 1400px) {
    ul {
      width: 90vw;
    }
  }
</style>

<header>
  <ul>
    <li on:click={goToHome}>SvelteCommerce</li>
    <li on:click={goToCheckout}>
      <img
        class="shopping-cart"
        aria-label="shopping cart"
        alt="Checkout"
        src="img/svg/checkout.svg"
        height="34px" />
      {#if cart_sum > 0}
        <div class="circle">{cart_sum}</div>
      {/if}
    </li>
  </ul>
</header>
