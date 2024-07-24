<script lang="ts">
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
    <h1>Hair Image Curvature Analysis</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      As part of my research with Dr. Tina Lasisi, I worked on updating the
      Fibermorph project which is a project that is used for determining the
      length and curvature of human hairs given microscopic images of them.
      There were three main goals with improving the analysis: improve the ease
      of use, improve the accuracy, and improve the speed. Addressing these
      required coming up with new algorithmic approaches, as well as figuring
      out methods for generating realistic testing data. This discusses some,
      but not all of what went into the project.
    </p>
  </div>

  <div class="content">
    <div class="section">
      <div class="text">
        <h2>Algorithmic Problem</h2>
        <p>
          The overall problem is to take a noisy image from a microscope, that
          includes some approximately circular arcs, and identify the arcs and
          calculate a best fit. There are a few challenges with this specific
          task. The arcs often overlap, they can occasionally have a bend (which
          should be treated as two separate arcs), they're blurry, and there can
          be small gaps.
        </p>
        <p>
          Because the problem was challenging, a few approaches were evaluated.
          The first idea was to use a variant of the Hough transform, modified
          for circular arcs, much like is done in <a
            href="https://www.sciencedirect.com/science/article/abs/pii/016786559580007G"
          >
            this paper</a
          >. However, this struggled if the arcs ended up being more elliptical
          in practice. The second method was to skeletonize each line, and then
          experiment with all feasible endpoint combinations and attempt
          classical curve fitting. This approach requires many more heuristics,
          but proved better in the worst cases.
        </p>
      </div>
      <!-- <div class="image">
        <figure>
          <img
            src={best_board}
            alt="Best Boggle Board"
            style="width:105%; max-width:105%"
          />
          <figcaption>The highest scoring 4x4 Word Hunt board</figcaption>
        </figure>
      </div> -->
    </div>

    <div class="section">
      <div class="text">
        <h2>Algorithm Evaluation</h2>
        <p>
          Part of the challenge with this project was the difficulty in
          evaluating new approaches. In addition to improving the UI for
          checking analyses, a priority was placed on generating realistic data
          with known "correct" results. For this, a UI was built out that
          supports custom generating images with different levels of noise,
          blur, color variance, scratches, and types of arcs. For proper
          testing, we need to control whether or not arcs have "bends", how
          circular/elliptical they are, the clarity and thickness of the arcs,
          and the level of overlap.
        </p>
      </div>
      <!-- <div class="image">
        <figure>
          <img
            src={hill_climb}
            alt="Hill Climb Animation"
            style="width:105%; max-width:105%"
          />
          <figcaption>Hill Climbing approach on a random board</figcaption>
        </figure>
      </div> -->
    </div>

    <div class="text">
      <h2>How It Was Made</h2>
      <p>
        The project was built using python with Numpy to support efficient
        vectorized operations. Some operations from scikit-image were also used
        to improve image quality. Tkinter was used to create all of the UI
        components.
      </p>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information, visit the project on <a
        href="https://github.com/bizy-coder/OptimalBoggleBoard"
        target="_blank">GitHub</a
      >.
    </p>
  </div>
</div>
<Modal bind:showModal>
  {#if activeModal}
    <img src={activeModal.src} alt={activeModal.alt} />
  {/if}
</Modal>
