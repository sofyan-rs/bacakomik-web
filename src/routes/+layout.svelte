<script lang="ts">
  import "../app.css";
  import Header from '$lib/components/header.svelte';
  import Footer from '$lib/components/footer.svelte';
</script>

<Header />

<section class="container mx-auto px-5 py-10">
  <slot />
</section>

<Footer />