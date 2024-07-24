<script lang="ts">
  // Import images if needed
  // import expression_tree from "$lib/assets/expression_tree.png";
  // import physics_equation from "$lib/assets/physics_equation.gif";
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
    <h1>Physics Calculator</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      This project implements an advanced Expression Tree parser in pure Python,
      featuring a sophisticated pattern matching system. It's capable of
      performing complex mathematical operations including derivatives,
      algebraic simplifications, and variable substitutions. As a practical
      application, the system can handle first-year physics with calculus
      equations, solving for unknown variables, combining and solving systems of
      equations, and converting between different units.
    </p>
  </div>

  <div class="content">
    <div class="section">
      <div class="text">
        <h2>The Challenge</h2>
        <p>
          Traditional calculator projects in introductory Data Structures
          courses often lack the ability to perform algebraic manipulations or
          handle complex transformations. As a teaching assistant for such a
          course, I aimed to create a more challenging and less publicly
          accessible project that could integrate concepts from concurrent
          Calculus courses.
        </p>
        <p>
          While the initial goal was to incorporate derivative calculations, the
          project's complexity exceeded the scope of the introductory course.
          This led to the expansion of the project into a more comprehensive and
          flexible system.
        </p>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={expression_tree}
            alt="Expression Tree"
            style="width:105%; max-width:105%"
          />
          <figcaption>Visualization of an Expression Tree</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>The Solution</h2>
        <p>
          The core of this project is a generic pattern matching system that
          allows for versatile manipulation of mathematical expressions. Key
          features include:
        </p>
        <ul>
          <li>
            Expression Tree parsing for arbitrary complex mathematical
            operations
          </li>
          <li>Pattern matching system for flexible equation manipulation</li>
          <li>
            Ability to perform derivatives, algebraic simplifications, and
            variable substitutions
          </li>
          <li>
            Application to physics equations, including solving for unknowns and
            unit conversions
          </li>
        </ul>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={physics_equation}
            alt="Physics Equation Solving"
            style="width:105%; max-width:105%"
          />
          <figcaption>Solving a complex physics equation</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="text">
      <h2>Implementation and Future Potential</h2>
      <p>
        The approach used in this project is similar to how Abstract Syntax
        Trees are parsed in many programming languages. It also shares
        fundamental principles with advanced Computer Algebra Systems (CAS) like
        Wolfram-Alpha or Sage Math. The main difference lies in the
        implementation of clever heuristics for Expression Tree manipulation,
        which are crucial for efficient equation handling in full-fledged CAS
        systems.
      </p>
      <p>
        While the current implementation relies on brute-force methods for
        manipulating equations, which can be slow for complex expressions, it
        provides a solid foundation for further development. With the addition
        of more sophisticated heuristics, this system could potentially evolve
        into a powerful tool for mathematical and physical computations.
      </p>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information and to explore the code, visit the project on
      <a href="https://github.com/bizy-coder/physics-calculator" target="_blank"
        >GitHub</a
      >.
    </p>
  </div>
</div>
<Modal bind:showModal>
  {#if activeModal}
    <img src={activeModal.src} alt={activeModal.alt} />
  {/if}
</Modal>
