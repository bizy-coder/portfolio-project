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
    <h1>Backdoor Image Poisoning</h1>
  </div>

  <div class="overview">
    <p></p>
  </div>

  <div class="content"></div>

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
