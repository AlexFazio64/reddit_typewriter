<script>
  import { theme, font } from "./stores";
</script>

{#if $theme == "dark"}
  <style>
    :root {
      /* dark */
      --color: white;
      --bg-color: hsl(0, 0%, 13%);
      --bg-color-hover: hsl(0, 0%, 17%);
      --bg-scroll: hsl(0, 0%, 30%);
    }
  </style>
{:else}
  <style>
    :root {
      /* light */
      --color: hsl(0, 0%, 13%);
      --bg-color: white;
      --bg-color-hover: hsl(0, 0%, 90%);
      --bg-scroll: hsl(0, 0%, 70%);
    }
  </style>
{/if}

{#if $font == "Roboto Serif"}
  <style>
    :root {
      --font: "Roboto Serif", monospace;
    }
  </style>
{:else}
  <style>
    :root {
      --font: "Freehand", serif;
    }
  </style>
{/if}
