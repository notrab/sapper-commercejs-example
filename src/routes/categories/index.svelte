<script context="module">
  import commerce from "../../lib/commerce.js";

  export async function preload() {
    const { data: categories } = await commerce.categories.list();

    return {
      categories,
    };
  }
</script>

<script>
  export let categories;
</script>

<h1>Categories</h1>

<ul>
  {#each categories as category}
    <li>
      <a rel="prefetch" href="categories/{category.slug}">{category.name}</a>
    </li>
  {/each}
</ul>
