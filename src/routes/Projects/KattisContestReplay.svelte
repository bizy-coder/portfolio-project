<script lang="ts">
  // Import images if needed
  // import kattis_logo from "$lib/assets/kattis_logo.png";
  // import contest_replay from "$lib/assets/contest_replay.gif";

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
    <h1>Kattis Contest Replay</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      Kattis is a popular platform for competitive programming, but it lacks a
      feature to replay past contests. This project addresses that gap by
      creating a website that combines multiple Kattis contests, allowing users
      to compare contests or practice alongside a replayed scoreboard as if they
      were part of the original event.
    </p>
  </div>

  <div class="content">
    <div class="section">
      <div class="text">
        <h2>The Challenge</h2>
        <p>
          While Kattis excels in hosting competitive programming contests, the
          inability to replay past events poses a significant limitation for
          practice and analysis. This feature is particularly crucial for
          schools and competitive programmers looking to improve their skills by
          simulating real contest environments.
        </p>
        <p>
          Our school faced this challenge multiple times last year, highlighting
          the need for a solution that would allow students to experience the
          dynamic nature of a live scoreboard while practicing with past contest
          problems.
        </p>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={kattis_logo}
            alt="Kattis Logo"
            style="width:105%; max-width:105%"
          />
          <figcaption>Kattis: A platform for competitive programming</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>The Solution</h2>
        <p>
          To address this need, I developed a Sveltekit app that serves as a
          comprehensive contest replay platform. The solution consists of two
          main components:
        </p>
        <ul>
          <li>
            <strong>Backend:</strong> A system that makes requests to the appropriate
            Kattis contest webpages, scrapes the incoming data, and formats it into
            a JSON structure for easy processing.
          </li>
          <li>
            <strong>Frontend:</strong> A user interface built with the help of Shadcn-Svelte,
            providing an intuitive and visually appealing way to view contest standings
            and navigate through the replay.
          </li>
        </ul>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={contest_replay}
            alt="Contest Replay Interface"
            style="width:105%; max-width:105%"
          />
          <figcaption>The Kattis Contest Replay interface in action</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="text">
      <h2>Key Features</h2>
      <ul>
        <li>Ability to combine and compare multiple Kattis contests</li>
        <li>Real-time scoreboard evolution simulation</li>
        <li>User-friendly interface for easy navigation and analysis</li>
        <li>Seamless integration with existing Kattis contest data</li>
      </ul>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information and to contribute to the project, visit the
      <a
        href="https://github.com/bizy-coder/kattis-contest-replay"
        target="_blank">GitHub repository</a
      >.
    </p>
  </div>
</div>
<Modal bind:showModal>
  {#if activeModal}
    <img src={activeModal.src} alt={activeModal.alt} />
  {/if}
</Modal>
