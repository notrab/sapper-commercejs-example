<script context="module">
  import commerce from "../lib/commerce.js";

  export async function preload() {
    const merchant = await commerce.merchants.about();
    const { data: categories } = await commerce.categories.list();
    const { data: products } = await commerce.products.list();

    return {
      merchant,
      categories,
      products,
    };
  }
</script>

<script>
  export let merchant;
  export let categories;
  export let products;
</script>

<h1>{merchant.business_name}</h1>

<ul>
  {#each categories as category}
    <li>
      <a rel="prefetch" href="categories/{category.slug}">{category.name}</a>
    </li>
  {/each}
</ul>

<ul>
  {#each products as product}
    <li>
      <a rel="prefetch" href="products/{product.permalink}">{product.name}</a>
    </li>
  {/each}
</ul>
