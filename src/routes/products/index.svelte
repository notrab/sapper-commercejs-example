<script context="module">
  import commerce from "../../lib/commerce.js";

  export async function preload() {
    const { data: products } = await commerce.products.list();

    return {
      products,
    };
  }
</script>

<script>
  export let products;
</script>

<h1>Products</h1>

<ul>
  {#each products as product}
    <li>
      <a rel="prefetch" href="products/{product.permalink}">{product.name}</a>
    </li>
  {/each}
</ul>
