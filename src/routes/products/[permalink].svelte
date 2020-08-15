<script context="module">
  import commerce from "../../lib/commerce.js";

  export async function preload({ params }) {
    const { permalink } = params;

    const product = await commerce.products.retrieve(permalink, {
      type: "permalink",
    });

    return {
      product,
    };
  }
</script>

<script>
  export let product;
</script>

<h1>{product.name}</h1>

<p>{product.price.formatted_with_symbol}</p>
