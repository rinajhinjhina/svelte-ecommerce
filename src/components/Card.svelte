<script>
  export let img;
  export let name;
  export let price;

  img = `img/${img}`;
</script>

<style>
  .item-card {
    align-self: stretch;
    font-size: 10px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 180px 2fr 1fr;
    column-gap: 10px;
    max-width: 300px;
    padding: 2em;
    box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.3);
  }

  img {
    width: 100%;
    height: 180px;
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
    font-size: 1.3em;
    justify-self: end;
    align-self: center;
  }

  button {
    grid-column: 1/3;
    grid-row: 3;
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
</style>

<div class="item-card">
  <img src={img} alt={name} />
  <h3 class="title">{name}</h3>
  <p class="price">৳ {price}</p>
  <button>
    <object
      aria-label="shopping cart"
      type="image/svg+xml"
      data="img/svg/shopping-cart.svg" />
    Add to cart
  </button>
</div>
