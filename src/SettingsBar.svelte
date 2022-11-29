<script>
  import ChangeTheme from "./ChangeTheme.svelte";
  import ChangeType from "./ChangeType.svelte";
</script>

<nav>
  <ChangeType />
  <ChangeTheme />
</nav>

<style>
  nav {
    padding: 0.75em;
    position: fixed;
    top: 0;
    right: 50%;
    transform: translateX(50%);

    border-radius: 0 0 0.5em 0.5em;

    transition: all 0.25s ease-in-out;
    opacity: 0.25;

    display: flex;
    gap: 1em;
  }

  nav:hover {
    background-color: var(--bg-color);
    box-shadow: 0px 0px 10px 25px var(--bg-color);
    opacity: 1;
  }
</style>
