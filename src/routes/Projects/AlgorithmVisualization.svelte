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
    <h1>Algorithm Visualization</h1>
  </div>

  <div class="overview">
    <p>
      I built out a website for visualizing arbitrary algorithms, from dynamic
      programming to sorting and graphs, and from simple algorithms like bfs to
      complicated algorithms like suffix trees. This works by using Python's
      introspection to step through Python code line-by-line, and adding
      visualization commands that can be embedded into the Python.
    </p>
  </div>

  <div class="content">
    <p>
      From my experience teaching, I realized that one of the main challenges
      people had with algorithms was visualizing how they work. Often times, I'd
      end up looking for helpful websites to demonstrate algorithms, but all of
      them suffered from various issues. Thus, I decided it would be helpful to
      have one standardized website that supports every common algorithm.
      Furthermore, it occurred to me that while a very important skill, for
      complete beginners having to use a debugger was often a hurdle to learning
      programming. This inspired me to include line-by-line code visualization,
      which it turns out when combined with algorithm visualization is also
      really helpful for understanding what different parts of algorithms
      actually do.
    </p>
  </div>

  <div class="footer">
    <p>
      For more information, visit the project on <a
        href="https://github.com/bizy-coder/geolocation"
        target="_blank">Github</a
      >.
    </p>
  </div>
</div>
<Modal bind:showModal>
  {#if activeModal}
    <img src={activeModal.src} alt={activeModal.alt} />
  {/if}
</Modal>
