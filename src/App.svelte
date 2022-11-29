<script lang="ts">
  import { onMount } from "svelte";
  import Prefs from "./Prefs.svelte";
  import Author from "./Author.svelte";
  import SettingsBar from "./SettingsBar.svelte";

  const lorem: string =
    "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Unde, aliquam! Voluptatum quas quasi, odit quibusdam, corporis cupiditate quam at rem assumenda, modi voluptate atque facere similique molestiae ratione optio dicta ut eaque dolorem consequatur amet.";
  let typed: string = "";

  const type = async () => {
    //122 wpm 562 cpm
    const cpm: number = 1000;
    const wpm: number = 3000;
    const words: string[] = lorem.split(" ");

    // add words letter by letter to typed with a delay
    for (const c of lorem) {
      typed += c;
      await new Promise((resolve) => setTimeout(resolve, 60000 / cpm));
    }

    for (let i = 0; i < words.length; i++) {
      for (let j = 0; j < words[i].length; j++) {}
      typed += " ";
      await new Promise((resolve) => setTimeout(resolve, 60000 / wpm));
    }
  };

  const getPost = async () => {
    const response = await fetch("http://localhost:3004/posts/?id=1");
    const data = await response.text();

    if (response.ok) {
      const json = JSON.parse(data)[0];
      return json;
    }
  };

  onMount(() => {
    const obs = new ResizeObserver(() =>
      document.getElementById("anchor").scrollIntoView()
    );
    obs.observe(document.body);
    type();
  });
</script>

{#await getPost()}
  <p>loading</p>
{:then json}
  <h1>{json.title}</h1>
  <br />
{/await}

<Prefs />
<SettingsBar />

<p>{typed}</p>
<div id="anchor" />

<Author user="u/AlexFazio64" />

<style>
  h1 {
    align-self: start;
    font-family: var(--font);
    font-size: 3em;
  }
  p {
    font-size: 2.5em;
    line-height: 1.25em;
    justify-content: center;
    word-spacing: normal;
    font-family: var(--font);
  }
</style>
