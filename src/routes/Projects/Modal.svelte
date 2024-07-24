<script lang="ts">
  import { browser } from "$app/environment";

  export let showModal = false;

  let dialog: HTMLDialogElement;

  let modalShown = false;

  $: if (dialog && showModal) {
    dialog.showModal();
    setTimeout(() => {
      if (showModal) modalShown = true;
    }, 10);
  }

  function closeDialog() {
    if (dialog && showModal && modalShown) {
      dialog.close();
      modalShown = false;
    }
  }

  let scrollTop = 0;

  let scrollLeft = 0;

  function disableScroll() {
    if (browser) {
      scrollTop = window.scrollY || window.document.documentElement.scrollTop;
      (scrollLeft =
        window.scrollX || window.document.documentElement.scrollLeft),
        (window.onscroll = function () {
          window.scrollTo(scrollLeft, scrollTop);
        });
    }
  }

  function enableScroll() {
    if (browser) {
      window.onscroll = function () {};
    }
  }

  $: if (modalShown) {
    // document.addEventListener("keydown", handleKeydown);
    disableScroll();
  } else {
    // document.removeEventListener("keydown", handleKeydown);
    enableScroll();
  }
  function handleKeydown(event: KeyboardEvent): void {
    if (event.key === "Escape" && showModal) {
      closeDialog();
    }
  }
</script>

<svelte:window
  on:click={() => closeDialog()}
  on:keydown={(event) => handleKeydown(event)}
/>
<!-- <svelte:window /> -->

<!-- svelte-ignore a11y-click-events-have-key-events a11y-no-noninteractive-element-interactions -->
<dialog
  bind:this={dialog}
  on:close={() => (showModal = false)}
  on:click|self={() => closeDialog()}
  style="border:none"
>
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-content" on:click|stopPropagation>
    <span class="close-button" on:click={() => closeDialog()}>&times;</span>
    <slot name="header" />
    <slot />
    <!-- svelte-ignore a11y-autofocus -->
  </div>
</dialog>

<style>
  dialog {
    max-width: 80vw;
    max-height: 80vh;
    /* position: fixed; */
    /* top: 50%;
    left: 50%; */
    /* transform: translate(-50%, -50%); */
    border: none;
    padding: 0;
    background: none;
    overflow: visible;
  }
  dialog:focus-visible {
    outline: none;
  }
  dialog::backdrop {
    background: rgba(0, 0, 0, 0.8);
    pointer-events: none;
  }
  dialog > .modal-content {
    position: relative;
    display: flex;
    flex-direction: column;
    padding: 0;
    margin: 0;
    align-items: center;
    background: white;
  }
  /* dialog[open] {
    animation: zoom 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  }
  @keyframes zoom {
    from {
      transform: translate(-50%, -50%) scale(0.95);
    }
    to {
      transform: translate(-50%, -50%) scale(1);
    }
  }
  dialog[open]::backdrop {
    animation: fade 0.2s ease-out;
  }
  @keyframes fade {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  } */
  .close-button {
    position: absolute;
    top: -1.5em;
    right: 0;
    font-size: 3.5em;
    cursor: pointer;
    color: white;
  }
</style>
