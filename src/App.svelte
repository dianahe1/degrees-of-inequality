<script>
  import Section1 from "./sections/1-title.svelte";
  import Section2 from "./sections/2-gap.svelte";
  import Section3 from "./sections/3-college.svelte";
  import Section4 from "./sections/4-no-diff.svelte";
  import Section5 from "./sections/5-debt.svelte";
  import Section6 from "./sections/6-debt-facts.svelte";
  import Section7 from "./sections/7-generational.svelte";
  import Section8 from "./sections/8-conclude.svelte";
</script>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    scroll-behavior: smooth;
    overflow-x: hidden;
  }
</style>

<main>
  <Section1 />
  <Section2 />
  <Section3 />
  <Section4 />
  <Section5 />
  <Section6 />
  <Section7 />
  <Section8 />
</main>
