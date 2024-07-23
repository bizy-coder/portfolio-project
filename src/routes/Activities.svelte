<script>
  export let activities = [
    {
      title: "ICPC (Competitive Programming)",
      description: `I participated in my university's ICPC team while in college. In 2024, we advanced to the North American Championship for the first time in our school's history after I solved an <a href='https://naeast23.kattis.com/contests/naeast23/problems/impartialstrings' target="_blank" class="project-card">interesting problem on finite automata</a> in the last few minutes to beat out some schools like Harvard and Carnegie Mellon.<br><br>Through studying for ICPC I learned lots of advanced data structures and algorithms, but more importantly got significant practice with very difficult problem solving and debugging, particularly when working with a team.`,
    },
    {
      title: "Code Golf",
      description: `I'm very good at "Code Golf", where you write programs with the goal of them being as short as possible. In addition to running a Code Golf competition at my university, I like to compete on <a href='https://code.golf/intersection#python' target="_blank" class="project-card">code.golf</a>, where I own a couple first place solutions on long-standing problems in Python (out of ~300 people who tried, no one has been able to get a solution as short as mine). If you're reading this, I encourage you to give it a try!<br><br>Another great place to see this kind of code is with <a href='https://adventofcode.com' target="_blank" class="project-card">Advent of Code</a>. This is a month-long event in December every year with a programming puzzle each day. As an unofficial challenge, a group of people like to collaboratively golf these problems to the shortest code they can. I contributed extensively to these solutions last year, being the final improvement on many of them. You can find them all <a href='https://adventofcode.com' target="_blank" class="project-card">here</a>.`,
    },
    {
      title: "Science Olympiad <br/><p style='margin-top: 1.65em;'></p>",
      description:
        "As a founding member of Penn State's Science Olympiad organization, I helped plan and host a national science tournament for high school students. We launched with an online event during the Covid pandemic and transitioned to an in-person tournament in subsequent years.<br><br>The event grew to host over 600 students from 10 states. My roles included designing the website, serving as Treasurer, and planning all pre-awards activities. This experience honed my skills in large-scale event management, clear communication across diverse groups, and leadership.",
    },
    {
      title: "PSU Engineering Teaching & Research Experiences",
      description: `At Penn State, I was selected for UTREE (Undergraduate Teaching and Research Experiences in Engineering) through technical speaking contest all Engineering students participated in. As a UTREE member, I:
  <ul>
    <li>Participated in various technical development projects</li>
    <li>Mentored top engineering students on refining communication skills</li>
    <li>Planned and organized future speaking contests</li>
    <li>Delivered a presentation to students at McMaster University competing in the North American EcoCar championship</li>
  </ul>
  This experience enhanced my technical communication skills, mentorship abilities, and project management capabilities.`,
    },
    // {
    //   title: 'Chess',
    //   description: '...'
    // },
    // {
    //   title: 'Sports',
    //   description: '...'
    // }
  ];
</script>

<div class="activities-grid">
  {#each activities as activity, i}
    <div class="activity-cell">
      {#if i > 1}
        <h2 style="padding-top:1rem">{@html activity.title}</h2>
      {:else}
        <h2>{@html activity.title}</h2>
      {/if}
      <p>{@html activity.description}</p>
    </div>
  {/each}
</div>

<style>
  .activities-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr); /* Two columns of equal width */
  }

  .activity-cell {
    display: flex;
    flex-direction: column;
    border-right: 2px solid #ccc; /* Right border for cells */
    border-bottom: 2px solid #ccc; /* Bottom border for cells */
    padding: 0rem 1rem 1rem 0.2rem;
    margin: 0;
    /* line-height: 1rem; */
    box-sizing: border-box;
  }

  .activities-grid > :nth-last-child(-n + 2) {
    border-bottom: none; /* Remove bottom border for the last row */
    padding-bottom: 0rem;
    /* margin-top: 1rem; */
  }

  .activity-cell h2 {
    margin: 0 0 10px 0; /* Spacing below the title */
  }
  .activity-cell:nth-child(even) {
    border-right: 0px; /* Adjust right border for odd items */
    padding-right: 0.2rem;
    padding-left: 1rem;
  }

  .activity-cell p {
    margin: 0;
    flex-grow: 1; /* Ensures paragraph takes up the rest of the space */
    overflow: hidden; /* Prevents text overflow */
  }
</style>
