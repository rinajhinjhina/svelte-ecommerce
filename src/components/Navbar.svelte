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
    position: relative;
    display: flex;
    align-items: center;
  }

  ul li .shopping-cart {
    margin-left: 0.5em;
  }

  ul li .circle {
    position: absolute;
    border: 1px solid rgba(0, 0, 0, 0.5);
    top: -2px;
    right: -5px;
    background-color: #fff596;
    color: rgba(0, 0, 0, 0.8);
    padding: 0.1em;
    text-align: center;
    line-height: 1em;
    font-size: 0.4em;
    width: 1em;
    height: 1em;
    border-radius: 1em;
  }
</style>

<header>
  <ul>
    <li>SvelteCommerce</li>
    <li>
      <span>Checkout</span>
      <object
        class="shopping-cart"
        aria-label="shopping cart"
        type="image/svg+xml"
        height="17"
        data="img/svg/checkout.svg" />
      <div class="circle">1</div>
    </li>
  </ul>
</header>
