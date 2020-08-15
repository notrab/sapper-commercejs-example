<script context="module">
  import commerce from "../../lib/commerce.js";

  export async function preload({ params }) {
    const { slug } = params;

    const category = await commerce.categories.retrieve(slug, {
      type: "slug",
    });
    const { data: products } = await commerce.products.list({
      category_slug: slug,
    });

    return {
      category,
      products,
    };
  }
</script>

<script>
  export let category;
  export let products;
</script>

<h1>{category.name}</h1>

<ul>
  {#each products as product}
    <li>
      <a rel="prefetch" href="products/{product.permalink}">{product.name}</a>
    </li>
  {/each}
</ul>
