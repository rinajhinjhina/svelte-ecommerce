<script>
  import { cart } from "../stores/stores.js";

  let cartItems = [];
  const unsubscribe = cart.subscribe(
    items => (cartItems = Object.values(items))
  );

  console.log(cartItems);
</script>

<style>
  .checkout-container {
    width: 70vw;
    margin: 10vh auto 0 auto;
    display: flex;
    flex-direction: column;
  }

  .item-grid {
    display: flex;
  }

  img {
    width: 25%;
    height: 200px;
    object-fit: cover;
    margin: 10px 20px 10px 0;
  }

  .item-meta-data {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
  }

  .item-meta-data h3 {
    margin-top: 0;
  }

  .item-meta-data p {
    margin: 0.2em 0;
  }

  @media screen and (max-width: 1600px) {
    .checkout-container {
      width: 80vw;
    }
  }

  @media screen and (max-width: 1400px) {
    .checkout-container {
      width: 90vw;
    }
  }
</style>

<div class="checkout-container">
  <h1>My Cart</h1>
  {#each cartItems as item}
    <div class="item-grid">
      <img src={`img/${item.img}`} alt={item.name} />
      <div class="item-meta-data">
        <h3 class="title">{item.name}</h3>
        <p class="price">Price: ৳ {item.price}</p>
        <p class="count">Quantity: {item.count}</p>
      </div>
    </div>
  {/each}
</div>
