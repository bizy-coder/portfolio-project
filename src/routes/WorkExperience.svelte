<script>
  // Sample data for work experience
  let workExperience = [
    {
      company: 'Dr. Tina Lasisi Research Lab',
      role: 'Research Assistant',
      period: 'Apr 2020 - Current',
      description: ''
    },
    {
      company: 'Penn State: Introduction to Data Structures and Algorithms',
      role: 'Head Learning Assistant',
      period: 'Nov 2017 - Mar 2020',
      description: ''
    }
  ];
</script>

{#each workExperience as job, index}
  <div class:extra-gap={index > 0}>
    <h3>{job.company}</h3>
    <h4>{job.role} <span>({job.period})</span></h4>
    <p>{job.description}</p>
  </div>
{/each}

<style>
  /* div {
    margin-bottom: 2rem;
  } */
  .extra-gap {
    margin-top: 3rem;
  }
  h4 {
    margin: 0.15rem 0 1rem;
  }
  span {
    font-style: italic;
    font-weight: normal;
  }
  p {
    margin: 0.5rem 0;
  }
</style>
