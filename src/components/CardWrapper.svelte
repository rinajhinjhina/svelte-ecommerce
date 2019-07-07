<script>
  import Card from "./Card.svelte";
  import items from "../items.js";
</script>

<style>
  .grid-col-3 {
    width: 70vw;
    margin: 15vh auto;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
  }
</style>

<section class="card-wrapper grid-col-3">
  {#each items as item}
    <Card {...item} />
  {/each}
</section>
