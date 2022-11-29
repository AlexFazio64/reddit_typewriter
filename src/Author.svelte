<script>
  export let user = "";
</script>

<footer>
  <quote>Author</quote>
  <a href="https://www.reddit.com/{user}">{user}</a>
  <svg
    xmlns="http://www.w3.org/2000/svg"
    version="1.0"
    width="40px"
    height="40px"
    viewBox="0 0 1000 890"
    preserveAspectRatio="xMidYMid meet"
  >
    <path
      d="M353 876 c-156 -38 -278 -152 -287 -270 -2 -29 -11 -50 -29 -68 -48 -48 -44 -122 11 -171 28 -25 83 -32 117 -14 26 13 31 13 60 -4 46 -27 136 -56 198 -64 l54 -7 26 -126 c15 -69 31 -130 36 -135 6 -6 45 -3 101 8 87 17 91 17 111 -1 49 -44 139 -4 139 61 0 50 -33 85 -81 85 -38 0 -61 -15 -84 -54 -10 -17 -134 -51 -145 -39 -3 2 -14 49 -25 103 l-21 98 46 7 c67 10 137 32 185 58 37 21 45 23 66 11 72 -40 169 19 169 103 0 30 -33 93 -50 93 -5 0 -10 17 -10 38 0 23 -12 64 -31 101 -47 93 -147 162 -277 190 -68 14 -213 13 -279 -3z"
    />
  </svg>
  <a id="perma" href="https://www.reddit.com/">original post</a>
</footer>

<style>
  footer {
    position: fixed;
    padding: 0.75em;
    bottom: 0;
    right: 0;

    display: grid;
    grid-template-rows: repeat(3, 1fr);
    grid-template-columns: 2fr 1fr;

    gap: 0.5em 1em;

    border-radius: 0.5em 0 0 0;

    transition: all 0.25s ease-in-out;
    opacity: 0.25;
  }

  footer:hover {
    background-color: var(--bg-color);
    box-shadow: 0px 0px 10px 25px var(--bg-color);
    opacity: 1;
  }

  quote {
    grid-column: 1 / 3;
    justify-self: center;
  }

  svg {
    grid-row: 2 / 4;
    grid-column: 2 / 3;
    width: 40px;
    aspect-ratio: 1/1;
    fill: #ff4500;
  }

  a,
  a:visited {
    color: var(--color);
  }
</style>
