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
  <div class="projects-container" style="width:600px">
    {#each projects as project}
      <a href={project.url} target="_blank" class="project-card">
        <h3>{project.title}</h3>
        <p>{project.description}</p>
      </a>
    {/each}
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

  .project-card {
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 14px;
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
