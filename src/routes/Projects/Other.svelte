<script lang="ts">
  // Import images if needed
  // import project_collage from "$lib/assets/project_collage.png";
  import Modal from "./Modal.svelte";

  let activeModal: { src: string; alt: string } | null = null;
  let showModal = false;

  function openModal(imageSrc: string, imageAlt: string): void {
    activeModal = { src: imageSrc, alt: imageAlt };
    showModal = true;
  }
</script>

<div class="container">
  <div class="header">
    <h1>Other Projects</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      Beyond the featured projects, I've worked on a variety of other
      interesting and challenging projects across different domains. While these
      projects may not have dedicated pages due to various reasons (including
      having a hard drive crash on me, similarity to other projects, or having
      created them for university course assignments), they represent a diverse
      range of my skills and interests in computer science and artificial
      intelligence.
    </p>
  </div>

  <div class="content">
    <div class="text">
      <h2>Games AI</h2>
      <ul>
        <li>
          Genetic Algorithm for evolving 2048 heuristics used in a expectimax
          search, achieving a 95% win rate and able to provide human player
          feedback
        </li>
        <li>
          Reinforcement learning for a <a
            href="https://grgrdvrt.com/codevember_2019/9_game/"
            >Tetris + Snake" hybrid game</a
          >
        </li>
        <li>Alpha-beta search with PyTkinter visualization for Reversi</li>
        <li>
          Simulation analysis of many different games, most notably for Dominion
        </li>
      </ul>
    </div>
    <div class="text">
      <h2>Research-Oriented AI</h2>
      <ul>
        <li>In depth research presentations on AI security papers</li>

        <li>Multiple different adversarial example attacks on MNIST images</li>
        <li>Implementation of Neural Cellular Automata with interactive UI</li>
        <li>CNNs in NumPy with model visualization</li>
        <li>
          Genetic Algorithms for optimizing clustering algorithms by applying
          transformations to each dimension separately, applied to sports
          predictions
        </li>
      </ul>
    </div>

    <div class="text">
      <h2>Web Scraping and Data Analysis</h2>
      <ul>
        <li>
          Parsing 30+ years of somewhat unstandardized 10-K annual reports for
          financial research
        </li>
        <li>
          YouTube API data extraction and channel prediction via community
          analysis
        </li>
        <li>
          Standardizing Quiz Bowl questions from various PDF formats into JSON
          files
        </li>
        <li>
          Facebook Messenger log analysis for communication patterns and
          sentiment
        </li>
      </ul>
    </div>
    <div class="text">
      <h2>Video Analysis</h2>
      <ul>
        <li>
          Automatic sports highlight extraction based on crowd audio levels
        </li>
        <li>Zoom Office Hour content optimization by removing downtime</li>
      </ul>
    </div>

    <div class="text">
      <h2>Other Projects I found Fun</h2>
      <ul>
        <li>
          Python AST modification to make quick testing easier. Specifically
          improving debugging and at run time changing floating point operations
          to Fractions calculations
        </li>
        <li>
          ASCII art image and video converter, including a fully ascii art video
          player
        </li>
        <li>Simple assembly-like language interpreter</li>
        <li>
          Brainf*** JIT compiler and code generator with different heuristics
          and string algorithms for short code generation
        </li>
      </ul>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information about these or other projects, please <a
        href="mailto:zydney.biz11@gmail.com">contact me</a
      >.
    </p>
  </div>
</div>
<Modal bind:showModal>
  {#if activeModal}
    <img src={activeModal.src} alt={activeModal.alt} />
  {/if}
</Modal>
