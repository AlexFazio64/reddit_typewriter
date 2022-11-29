<script lang="ts">
  import { onMount } from "svelte";
  import ChangeTheme from "./ChangeTheme.svelte";
  import ChangeType from "./ChangeType.svelte";

  const lorem: string =
    "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Unde, aliquam! Voluptatum quas quasi, odit quibusdam, corporis cupiditate quam at rem assumenda, modi voluptate atque facere similique molestiae ratione optio dicta ut eaque dolorem consequatur amet. Aspernatur qui iure dolor iste necessitatibus commodi facere ipsam minus beatae laudantium ratione, numquam quo magni ipsum porro, et eos. Facilis libero distinctio possimus, perferendis est ipsam, beatae iste dolores cumque quam aliquam mollitia minima velit suscipit modi harum blanditiis maiores deserunt exercitationem asperiores! Ipsum delectus harum consequatur hic quod nam ducimus dignissimos quibusdam maiores iusto non rerum excepturi aperiam iure ratione laboriosam laborum aut, omnis error. Sapiente accusamus quae cumque possimus suscipit placeat, eaque vel debitis perspiciatis sit hic facilis omnis ab saepe nihil numquam dolores optio id voluptate soluta recusandae. Temporibus recusandae sequi vero minima eveniet laboriosam sunt fugit unde architecto id. Autem, assumenda eaque corrupti et culpa repellat quo, exercitationem incidunt itaque corporis amet, ipsam quam aliquam doloremque nulla sit voluptate facere. Obcaecati provident dolore, quas nesciunt consequuntur nam maiores odio nobis ex dicta reprehenderit non itaque. Nisi ducimus ab quaerat perferendis dolores repellendus consectetur officia, eaque natus sit aspernatur quo numquam debitis, quidem excepturi rem iusto, libero quisquam. Unde laudantium hic necessitatibus beatae, aliquid placeat consequatur laborum fugiat, rem, dolorem cumque odio dolore voluptates perferendis vero neque harum molestias maiores officiis! Quibusdam amet recusandae accusantium labore sequi blanditiis explicabo, quas commodi quidem quo asperiores doloremque sapiente voluptate exercitationem temporibus, atque alias at est molestias, ad assumenda dicta? Laborum ea officia, obcaecati recusandae porro praesentium nisi delectus beatae odit! Amet tempora fugiat error eveniet corrupti, suscipit est adipisci, velit quibusdam magnam non accusamus mollitia soluta libero aperiam expedita atque debitis molestiae rem incidunt laudantium. Dolorem culpa voluptas eum enim harum quibusdam quidem veniam atque a esse obcaecati autem iusto unde, exercitationem asperiores, expedita nostrum magnam nesciunt neque corporis quisquam, mollitia nisi. Repellat cum atque corporis ut, tempore veritatis nam sunt laudantium? Impedit porro nam natus odio labore, quibusdam iure illum vero debitis eveniet maiores dolor illo reprehenderit unde, eaque esse ut? Ab doloribus eum itaque incidunt quidem molestiae, fugiat ullam, eaque officiis porro ipsum nulla sequi inventore vel dolores natus, quam nostrum excepturi. Iste nisi blanditiis voluptas eum praesentium adipisci eaque cum quas, a, reiciendis perferendis sapiente corporis! Totam excepturi dolor dolorem doloribus quis accusantium nihil repudiandae, dolores iure, natus saepe cupiditate incidunt a neque in soluta rerum alias expedita? Enim, beatae.";
  let typed: string =
    "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Unde, aliquam! Voluptatum quas quasi, odit quibusdam, corporis cupiditate quam at rem assumenda, modi voluptate atque facere similique molestiae ratione optio dicta ut eaque dolorem consequatur amet. Aspernatur qui iure dolor iste necessitatibus commodi facere ipsam minus beatae laudantium ratione, numquam quo magni ipsum porro, et eos.Lorem, ipsum dolor sit amet consectetur adipisicing elit. Unde, aliquam! Voluptatum quas quasi, odit quibusdam, corporis cupiditate quam at rem assumenda, modi voluptate atque facere similique molestiae ratione optio dicta ut eaque dolorem consequatur amet.";

  const type = async () => {
    //122 wpm 562 cpm
    const cpm: number = 1000;
    const wpm: number = 3000;
    const words: string[] = lorem.split(" ");

    // add words letter by letter to typed with a delay
    for (const c of lorem) {
      typed += c;
      await new Promise((resolve) => setTimeout(resolve, 60000 / cpm));

      //scroll to bottom
      document.getElementById("letter").scrollIntoView();
    }

    for (let i = 0; i < words.length; i++) {
      for (let j = 0; j < words[i].length; j++) {}
      typed += " ";
      await new Promise((resolve) => setTimeout(resolve, 60000 / wpm));
    }
  };

  // onMount(type);
</script>

<nav>
  <ChangeType />
  <ChangeTheme />
</nav>

<p id="letter">
  {typed}
</p>
<quote>Author:</quote>
<quote><a href="https://www.reddit.com/u/AlexFazio64">AlexFazio64</a></quote>

<style>
  quote {
    align-self: end;
  }

  p {
    font-size: 3em;
    line-height: 1.25em;
    justify-content: center;
    word-spacing: normal;
  }

  nav {
    padding: 0.75em;
    position: fixed;
    top: 0;
    right: 50%;
    transform: translateX(50%);

    background-color: hsl(0, 0%, 13%);
    border-radius: 0 0 0.5em 0.5em;

    transition: all 0.25s ease-in-out;
    opacity: 0.25;

    display: flex;
    gap: 1em;
  }

  nav:hover {
    box-shadow: 0px 0px 10px 25px hsl(0, 0%, 13%);
    opacity: 1;
  }
</style>
