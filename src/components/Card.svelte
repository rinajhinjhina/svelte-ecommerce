<script>
  import { get } from "svelte/store";
  import { cart } from "../stores/stores.js";

  export let item;
  let { img, name, price } = item;
  img = `img/${img}`;

  const cartItems = get(cart);
  let inCart = cartItems[name] ? cartItems[name].count : 0;

  function addToCart() {
    inCart++;
    cart.update(n => {
      return { ...n, [name]: { ...item, count: inCart } };
    });
  }
</script>

<style>
  .item-card {
    align-self: stretch;
    justify-self: stretch;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 300px 0.5fr 0.5fr;
    column-gap: 10px;
    padding: 2em;
    font-size: 15px;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
  }

  img {
    width: 100%;
    height: 300px;
    object-fit: cover;
    grid-column: 1/4;
    grid-row: 1;
  }

  .title {
    align-self: center;
    font-size: 1.5em;
    grid-column: 1/3;
    grid-row: 2;
  }

  .price {
    grid-column: 3;
    grid-row: 2;
    font-size: 1.1em;
    justify-self: end;
    align-self: center;
  }

  .button-group {
    grid-column: 1/4;
    grid-row: 3;
    display: flex;
    align-content: center;
  }

  button {
    font-size: 1.2em;
    display: flex;
    align-self: end;
    justify-self: start;
    background: #20447d;
    color: white;
    text-align: center;
    cursor: pointer;
    padding: 0.4em 1.1em;
    border-radius: 5px;
    box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
  }

  button:focus {
    box-shadow: none;
    box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.6);
  }

  button object {
    margin-right: 0.5em;
    height: 1.2em;
  }

  .button-group span {
    align-self: center;
    color: rgba(0, 0, 0, 0.5);
    margin-left: 1em;
    font-size: 0.8em;
  }

  /* @media screen and (max-width: 880px){
    .button-group{

    }
  } */
</style>

<div class="item-card">
  <img src={img} alt={name} />
  <h3 class="title">{name}</h3>
  <p class="price">৳ {price}</p>
  <div class="button-group">
    <button on:click={addToCart}>
      <object
        aria-label="shopping cart"
        type="image/svg+xml"
        data="img/svg/shopping-cart.svg" />
      Add to cart
    </button>
    {#if inCart > 0}
      <span>
        <em>({inCart} in cart)</em>
      </span>
    {/if}
  </div>
</div>
