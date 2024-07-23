<script>
  // Sample data for work experience
  let workExperience = [
    {
      company: "Penn State: Introduction to OOP and Data Structures",
      role: "Head Learning Assistant",
      period: "June 2021 - May 2024",
      description: `As the lead Learning Assistant for a class of 600 students, I:
        <ul style="margin-top:0.25rem">
          <li>Created and delivered presentations on complex data structures topics</li>
          <li>Led lectures, recitations, and provided one-on-one support during office hours</li>
          <li>Collaborated closely with the professor to design engaging course content</li>
          <ul>
            <li>Developed over 30 new, original programming projects to enhance the curriculum</li>
            <li>Crafted exam questions to test critical understanding of the material</li>
          </ul>
          <li>Independently organized and ran the class's main extra credit opportunity - a code golf challenge</li>
        </ul>`,
    },
    {
      company: "Dr. Tina Lasisi Research Lab",
      role: "Research Assistant",
      period: "August 2021 - December 2023",
      description: `In Dr. Lasisi's anthropology research lab, I:
        <ul style="margin-top:0.25rem">
          <li>Led the redesign of Fibermorph, a program for analyzing microscopic hair images:
            <ul>
              <li>Improved performance by over 100 times</li>
              <li>Added capabilities to handle overlapping hairs</li>
            </ul>
          </li>
          <li>Contributed to multiple research papers on computational approaches to anthropological issues</li>
          <li>Performed data analysis in R and Excel, creating insightful visualizations </li>
          <li>Bridged anthropological and computational perspectives in interdisciplinary meetings at Yale</li>
          <li>Spearheaded the lab's transition to a Notion database, enhancing organization and workflow efficiency</li>
        </ul>`,
    },
  ];
</script>

{#each workExperience as job, index}
  <div class:extra-gap={index > 0}>
    <h3>{job.company}</h3>
    <h4>{job.role} <span>({job.period})</span></h4>
    <p>{@html job.description}</p>
  </div>
{/each}

<style>
  /* div {
    margin-bottom: 2rem;
  } */

  .extra-gap {
    margin-top: 1.5rem;
  }
  h4 {
    margin: -0.2rem 0 0.5rem;
    padding: 0;
  }
  h3 {
    margin: 0;
    padding: 0;
  }
  span {
    font-style: italic;
  }
</style>
