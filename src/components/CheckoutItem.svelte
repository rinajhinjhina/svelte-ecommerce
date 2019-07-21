<script>
  import { cart } from "../stores/stores.js";
  export let item;
  let { name, price, img, count } = item;

  const countButtonHandler = e => {
    if (e.target.classList.contains("add")) {
      count++;
    } else if (count >= 1) {
      count--;
    }
    cart.update(n => ({ ...n, [name]: { ...n[name], count } }));
  };

  const removeItem = () => {
    cart.update(n => {
      delete n[name];
      return n;
    });
  };
</script>

<style>
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
    font-size: 0.8em;
  }

  .count {
    display: flex;
    margin-top: 10px;
  }

  .count > * {
    display: block;
    margin: 0;
    font-size: 0.8em;
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
  }

  .count button.add {
    padding: 0.2em 0.4em;
    border-radius: 5px 0 0 5px;
    margin-right: 0;
    border: 0.5px solid #7d7d7d;
  }

  .count p {
    border: 0.5px solid #7d7d7d;
    margin: 0;
    padding: 0.2em 0.4em;
    background: #fefefe;
    border-left: none;
    border-right: none;
  }

  .count button.subtract {
    border: 0.5px solid #7d7d7d;
    padding: 0.2em 0.4em;
    border-radius: 0 5px 5px 0;
  }

  .count button.remove {
    display: flex;
    align-content: center;
    font-size: 0.6em;
    background-color: #c91616;
    color: white;
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
    margin-left: 10px;
  }

  .count button.remove object {
    width: 20px;
    height: 20px;
  }

  button > *:active,
  button > *:focus {
    outline: none;
  }

  @media screen and (max-width: 1048px) {
    img {
      width: 45%;
    }
  }

  @media screen and (max-width: 454px) {
    .item-grid {
      flex-direction: column;
    }

    img {
      width: 100%;
    }
  }
</style>

<div class="item-grid">
  <img src={`img/${img}`} alt={name} />
  <div class="item-meta-data">
    <h3 class="title">{name}</h3>
    <p class="price">Price: ৳ {price}</p>
    <div class="count">
      <button class="add" on:click={countButtonHandler}>+</button>
      <p>{count}</p>
      <button class="subtract" on:click={countButtonHandler}>-</button>
      <button class="remove" on:click={removeItem}>
        <object
          aria-label="remove"
          type="image/svg+xml"
          data="img/svg/cancel.svg" />
        Remove
      </button>
    </div>
  </div>
</div>
