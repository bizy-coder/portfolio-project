<script>
  export let activities = [
    {
      title: "ICPC (Competitive Programming)",
      description: `I participated in my university's ICPC team while in college. In 2024, we advanced to the North American Championship for the first time in our school's history after I solved an <a href='https://naeast23.kattis.com/contests/naeast23/problems/impartialstrings' target="_blank" class="project-card">interesting problem on finite automata</a> in the last few minutes to beat out some schools like Harvard and Carnegie Mellon.<br><br>Through studying for ICPC I learned lots of advanced data structures and algorithms, but more importantly got significant practice with very difficult problem solving and debugging, particularly when working with a team.`,
    },
    {
      title: "Code Golf",
      description: `I'm very good at "Code Golf", where you write programs with the goal of them being as short as possible. In addition to running a Code Golf competition at my university, I like to compete on <a href='https://code.golf' target="_blank" class="project-card">code.golf</a>, where I own a couple first place solutions on long-standing problems in Python (out of ~300 people who tried, no one has been able to get a solution as short as mine). If you're reading this, I encourage you to give it a try!<br><br>Another great place to see this kind of code is with <a href='https://adventofcode.com' target="_blank" class="project-card">Advent of Code</a>. This is a month-long event in December every year with a programming puzzle each day. As an unofficial challenge, a group of people like to collaboratively golf these problems to the shortest code they can. I contributed extensively to these solutions last year, being the final improvement on many of them. You can find them all <a href='https://adventofcode.com' target="_blank" class="project-card">here</a>.`,
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
  {#each activities as activity}
    <div class="activity-cell">
      <h2>{activity.title}</h2>
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
    box-sizing: border-box;
  }

  .activities-grid > :nth-last-child(-n + 2) {
    border-bottom: none; /* Remove bottom border for the last row */
    padding-bottom: 0rem;
    margin-top: 1rem;
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
