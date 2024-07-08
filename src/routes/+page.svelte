<script>
  import Header from '../lib/components/NavBar.svelte';
  // import Posts from './Posts.svelte';
  import WorkExperience from './WorkExperience.svelte';
  import Projects from './Projects.svelte';
  import Activities from './Activities.svelte';
</script>

<main>
  <Header />
  <div style="margin-bottom:8rem"> </div>

  <div class="header-container">
    <!-- <h1 class="my-name">Steven Leabo</h1> -->
     <!-- 🖐️ -->
    <h2 class="intro">Hi, I'm Ben <span class="wave">👋</span></h2>
    <p class="description">I'm a recent Computer Science graduate from Penn State, who loves programming and puzzles and is planning to turn it into a career. I'm particularly interested in Algorithms and AI (especially AI security!), but also have done some work with graphics and compilers. I graduated May 2024 with my Master's and am now looking for Software Engineering, quantitative trading, or AI Researcher jobs. If you are interested in collaborating with me or have any questions, you're more than welcome to reach out to me on <a href="https://www.linkedin.com/in/ben-zydney/"  target="_blank" rel="noopener noreferrer">Linkedin</a> or via email (<a href="mailto:zydney.biz11@gmail.com" target="_blank" rel="noopener noreferrer">zydney.biz11@gmail.com</a>).</p>
  </div>


  <!-- <section id="blog">
    <h2>Latest posts</h2>
    <Posts />
  </section> -->
  <section id="work">
    <h2 class="section-header">Work Experience</h2>
    <WorkExperience />
  </section>
  <section id="projects">
    <h2 class="section-header">Recent projects</h2>
    <Projects />
  </section>
  <section id="activities">
    <h2 class="section-header">Activities</h2>
    <Activities />
  </section>
</main>

<style>
.wave {
    -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
    display: inline-block;
  vertical-align: middle; /* Ensure it aligns properly with the text */

  position: relative;
  font-size: 20px;
  top: -4px;
  animation-name: wave-animation;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
}

@keyframes wave-animation {
    0% { transform: rotate( 0.0deg) }
   10% { transform: rotate(18.0deg) }  /* The following five values can be played with to make the waving more or less extreme */
   20% { transform: rotate(-8.0deg) }
   30% { transform: rotate(22.0deg) }
   40% { transform: rotate(-4.0deg) }
   50% { transform: rotate(14.0deg) }
   60% { transform: rotate( 0.0deg) }  /* Reset for the last half to pause */
  100% { transform: rotate( 0.0deg) }
}

  main {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: auto;
    /* padding: 1rem; */
  }
  section {
    margin-top: 2rem;
  }
  #work, #projects, #activities {
    margin-top: 4rem;
  }
  .section-header {
    border-bottom: 1px solid #ccc;
    padding-bottom: 0rem;
  }

  .header-container {
    max-width: 800px;
    margin: 3rem auto 0;
  }
  .intro {
    margin: 0.5rem 0;
  }

  .description {
    margin:0;
  }
</style>