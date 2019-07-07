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
  }

  ul li:last-child {
    display: flex;
    align-items: center;
  }

  ul li:last-child .shopping-cart {
    margin-right: 0.2em;
  }
</style>

<header>
  <ul>
    <li>SvelteCommerce</li>
    <li>
      <object
        class="shopping-cart"
        aria-label="shopping cart"
        type="image/svg+xml"
        height="17"
        data="img/svg/checkout.svg" />
      Checkout
    </li>
  </ul>
</header>
