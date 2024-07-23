<script>
  import { createEventDispatcher } from "svelte";

  export let src;
  export let alt;

  const dispatch = createEventDispatcher();

  function closeModal() {
    dispatch("close");
  }

  /**
   * @param {{ key: string; }} event
   */
  function handleKeydown(event) {
    if (event.key === "Escape") {
      closeModal();
    }
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="modal-overlay" on:click={closeModal}>
  <div class="modal-content" on:click|stopPropagation>
    <img {src} {alt} />
    <button class="close-button" on:click={closeModal}>×</button>
  </div>
</div>

<style>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal-content {
    position: relative;
    max-width: 90%;
    max-height: 90%;
  }

  img {
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
  }

  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    color: white;
    font-size: 24px;
    cursor: pointer;
  }
</style>
