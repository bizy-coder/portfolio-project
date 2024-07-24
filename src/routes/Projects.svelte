<script>
  // Sample data for projects
  let projects = [
    {
      title: "Optimal Boggle Board",
      description:
        "A heuristic based AI search for the boggle boards with the most words and the highest scores.",
      url: "/Projects?project=optimal-boggle",
    },
    {
      title: "Kattis Contest Replay",
      description:
        "A SvelteKit website to mirror competitions that happened previously on Kattis, a frequently used website for competitive programming practices.",
      url: "/Projects?project=kattis-contest-replay",
    },
    // Add more projects here
  ];
</script>

<div class="container">
  <div class="projects-container" style="max-width:600px">
    {#each projects as project}
      <a href={project.url} target="_blank" class="project-card">
        <h3>{project.title}</h3>
        <p>{project.description}</p>
      </a>
    {/each}
    <a class="view-all" href="/Projects">
      <span>V</span><span>i</span><span>e</span><span>w</span>
      <span> </span>
      <span>A</span><span>l</span><span>l</span>
      <span> </span>
      <span>P</span><span>r</span><span>o</span><span>j</span><span>e</span
      ><span>c</span><span>t</span><span>s</span>
    </a>
  </div>
</div>

<style>
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding-left: 0rem;
    padding-right: 0rem;
    padding-top: 0.5rem;
    padding-bottom: 0rem;
  }

  .projects-container {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    margin-bottom: 2rem;
  }

  .view-all {
    font-size: 1rem;
    /* background-color: #7a7878; */
    background-image: linear-gradient(to right, #4e4c4c, #5e6c6c);

    border: 1px solid #5e5c5c;
    color: white;
    border-radius: 1rem;
    padding: 0.6rem 0.9rem 0.6rem 0.9rem;
    text-decoration: none;
    text-align: center;
    margin: auto;
    /* width: calc(25% - 1rem); */
    width: 8.4rem;
    transition:
      transform 0.2s,
      box-shadow 0.2s;
    cursor: pointer;
  }

  .view-all:hover span {
    animation: dance 0.5s ease infinite alternate;
  }

  .view-all span {
    display: inline-block;
    transition: transform 0.8s ease;
  }

  .view-all:hover span:nth-child(1) {
    animation-delay: 0s;
  }
  .view-all:hover span:nth-child(2) {
    animation-delay: 0.05s;
  }
  .view-all:hover span:nth-child(3) {
    animation-delay: 0.1s;
  }
  .view-all:hover span:nth-child(4) {
    animation-delay: 0.15s;
  }
  .view-all:hover span:nth-child(5) {
    animation-delay: 0.2s;
  }
  .view-all:hover span:nth-child(6) {
    animation-delay: 0.25s;
  }
  .view-all:hover span:nth-child(7) {
    animation-delay: 0.3s;
  }
  .view-all:hover span:nth-child(8) {
    animation-delay: 0.35s;
  }
  .view-all:hover span:nth-child(9) {
    animation-delay: 0.4s;
  }
  .view-all:hover span:nth-child(10) {
    animation-delay: 0.45s;
  }
  .view-all:hover span:nth-child(11) {
    animation-delay: 0.5s;
  }
  .view-all:hover span:nth-child(12) {
    animation-delay: 0.55s;
  }
  .view-all:hover span:nth-child(13) {
    animation-delay: 0.6s;
  }
  .view-all:hover span:nth-child(14) {
    animation-delay: 0.65s;
  }
  .view-all:hover span:nth-child(15) {
    animation-delay: 0.7s;
  }
  .view-all:hover span:nth-child(16) {
    animation-delay: 0.75s;
  }
  .view-all:hover span:nth-child(17) {
    animation-delay: 0.8s;
  }

  .view-all:hover span {
    animation: dance 1.6s infinite;
  }

  @keyframes dance {
    0% {
      transform: translateY(0);
    }
    10% {
      transform: translateY(-5px);
    }
    25% {
      transform: translateY(0px);
    }
  }

  .view-all:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
  }

  .project-card {
    background-color: #f7f6f5;
    border: 1px solid #ddd;
    border-radius: 1rem;
    padding: 1rem;
    text-decoration: none;
    color: inherit;
    width: calc(100% - 1rem);
    transition:
      transform 0.2s,
      box-shadow 0.2s;
    cursor: pointer;
  }

  .project-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
  }

  h3 {
    margin: 0.5rem 0;
  }

  p {
    margin: 0;
  }
</style>
