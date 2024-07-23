<script lang="ts">
  import { onDestroy, onMount } from "svelte";
  import Header from "../../lib/components/NavBar.svelte";
  import Footer from "../../lib/components/x.svelte";
  import AirportDatabase from "./AirportDatabase.svelte";
  import AdversarialNLP from "./AdversarialNLP.svelte";
  import BackdoorAttacks from "./BackdoorAttacks.svelte";
  import Fibermorph from "./Fibermorph.svelte";
  import Geolocation from "./Geolocation.svelte";
  import KattisContestReplay from "./KattisContestReplay.svelte";
  import MaxLeafSpanningTree from "./MaxLeafSpanningTree.svelte";
  import OptimalBoggle from "./OptimalBoggle.svelte";
  import PhysicsCalculator from "./PhysicsCalculator.svelte";
  import Other from "./Other.svelte";
  import TandemRepeats from "./Other.svelte";

  let currentIndex = 0;
  let carouselContent: HTMLDivElement;
  let carouselContainer: HTMLDivElement;
  let components = [
    { component: OptimalBoggle, name: "Optimal Boggle" },
    { component: AirportDatabase, name: "Airport  Management System" },
    { component: Geolocation, name: "AI Geolocation" },
    { component: AdversarialNLP, name: "Adversarial NLP" },
    { component: Fibermorph, name: "Hair Analysis" },
    { component: KattisContestReplay, name: "Kattis Contest Replay" },
    { component: MaxLeafSpanningTree, name: "Maximum Leaf Trees" },
    { component: PhysicsCalculator, name: "Physics Calculator" },
    { component: Other, name: "Other Projects" },
    // { component: BackdoorAttacks, name: "Backdoor Attacks" },
    // { component: TandemRepeats, name: "Tandem Repeats" },
    // Add other components here
  ];
  let items = components.map((component) => component.component);
  let links = components.map((component) => component.name);

  let prevButton: HTMLButtonElement;
  let nextButton: HTMLButtonElement;

  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }

  function updateSlide(newIndex: number) {
    scrollToTop();
    const items = carouselContent.children;
    (items[currentIndex] as HTMLElement).style.opacity = "0";
    (items[currentIndex] as HTMLElement).style.display = "none";
    (items[newIndex] as HTMLElement).style.opacity = "1";
    (items[currentIndex] as HTMLElement).style.display = "flex";
    (carouselContent as HTMLElement).style.transform =
      `translateX(-${newIndex * 100}%)`;

    const currentItem = (
      (items[newIndex] as HTMLElement).querySelector(
        ".carousel-card"
      ) as HTMLElement
    ).querySelector(".card-content") as HTMLElement;
    const currentHeight =
      currentItem.getBoundingClientRect().height + 54 + "px";
    carouselContent.style.height = currentHeight;
    // carouselContainer.style.maxHeight = currentHeight;
    currentIndex = newIndex;
    updateButtonPositions();
  }

  function updateButtonPositions() {
    const carouselCard = document.querySelector(
      ".carousel-card"
    ) as HTMLElement;
    const carouselCardRect = carouselCard.getBoundingClientRect();
    const buttonOffset = 74; // Adjust this value to set the desired button height relative to the card top

    const topPosition = Math.max(
      carouselCardRect.top + buttonOffset,
      buttonOffset
    );

    prevButton.style.top = `${topPosition}px`;
    nextButton.style.top = `${topPosition}px`;
  }

  function next() {
    const newIndex = currentIndex < items.length - 1 ? currentIndex + 1 : 0;
    goToIndex(newIndex);
  }

  function previous() {
    const newIndex = currentIndex > 0 ? currentIndex - 1 : items.length - 1;
    goToIndex(newIndex);
  }

  function goToIndex(index: number) {
    updateSlide(index);
    const projectName = links[index].toLowerCase().replace(/\s+/g, "-");
    const newUrl = new URL(window.location.href);
    newUrl.searchParams.set("project", projectName);
    window.history.pushState({ index }, "", newUrl);
  }

  function handlePopState(event: PopStateEvent) {
    if (event.state && typeof event.state.index === "number") {
      updateSlide(event.state.index);
    } else {
      checkQueryParam();
    }
  }

  function checkQueryParam(): number {
    const urlParams = new URLSearchParams(window.location.search);
    const project = urlParams.get("project");
    if (project) {
      const index = links.findIndex(
        (link) => link.toLowerCase().replace(/\s+/g, "-") === project
      );
      if (index !== -1) {
        return index;
      }
    }
    return 0; // Default to first project if no valid query param
  }

  onMount(() => {
    const items = carouselContent.children;
    (items[currentIndex] as HTMLElement).style.opacity = "1"; // Fade out the current item
    carouselContent.style.transform = `translateX(0%)`;
    carouselContent.style.display = `flex`;
    updateSlide(0);
    updateButtonPositions();
    window.addEventListener("scroll", updateButtonPositions);
    window.addEventListener("resize", updateButtonPositions);

    window.addEventListener("popstate", handlePopState);

    const initialIndex = checkQueryParam();
    updateSlide(initialIndex);

    window.history.replaceState(
      { index: initialIndex },
      "",
      window.location.href
    );

    checkQueryParam();
  });

  onDestroy(() => {
    if (typeof window !== "undefined") {
      window.removeEventListener("popstate", handlePopState);
      window.removeEventListener("scroll", updateButtonPositions);
      window.removeEventListener("resize", updateButtonPositions);
    }
  });
</script>

<main>
  <Header width="700px" />

  <div style="margin-bottom:5rem"></div>

  <div class="selection-panel">
    <ul>
      {#each links as link, i}
        <li>
          <a href="javascript:void(0);" on:click={() => goToIndex(i)}>{link}</a>
        </li>
      {/each}
    </ul>
  </div>

  <div class="carousel-container" bind:this={carouselContainer}>
    <button
      class="carousel-button prev"
      on:click={previous}
      bind:this={prevButton}>❮</button
    >
    <div class="carousel-content" bind:this={carouselContent}>
      {#each items as Component, index}
        <div class="carousel-item">
          <div class="carousel-card">
            <div class="card-content">
              <Component />
            </div>
          </div>
        </div>
      {/each}
    </div>
    <button class="carousel-button next" on:click={next} bind:this={nextButton}
      >❯</button
    >
  </div>
  <Footer />
</main>

<style>
  main {
    font-family: Arial, sans-serif;
    max-width: 700px;
    margin: auto;
  }

  .selection-panel {
    margin-bottom: 1rem;
  }

  .selection-panel ul {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    list-style-type: none;
    padding: 0;
    margin: 0;
    text-align: center;
    text-decoration: underline;
  }

  .selection-panel li {
    margin-bottom: 0.5rem;
  }

  .selection-panel a {
    text-decoration: none;
    color: #007bff;
    font-weight: bold;
    cursor: pointer;
  }

  .selection-panel a:hover {
    text-decoration: underline;
  }

  a,
  a:link,
  a:visited {
    font-size: small;
    color: #919190;
    line-height: 1.5;
    margin: 0;
    padding: 0;
    transition:
      font-weight 0.1s ease,
      transform 0.1s ease;
  }

  a:hover {
    color: #585e68;
    text-shadow:
      0.1px 0 0 currentColor,
      -0.1px 0 0 currentColor,
      0 0.1px 0 currentColor,
      0 -0.1px 0 currentColor;
  }

  .carousel-container {
    position: relative;
    width: 100%;
    overflow: hidden;
    margin: auto;
  }

  .carousel-content {
    /* display: flex; */
    display: none;
    transition: transform 0.5s ease;
    transition: height 0.5s ease;
  }

  .carousel-item {
    min-width: 100%;
    transition: opacity 0.5s ease;
    opacity: 0;
  }

  .carousel-card {
    /* min-height: 20rem; */
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 24px;
    text-decoration: none;
    color: inherit;
    margin-left: 2px;
    width: calc(100% - 6px);
    /* cursor: pointer; */
  }

  .carousel-button {
    position: fixed;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    cursor: pointer;
    z-index: 1000;
    /* transition: top 0.3s ease; */
  }

  .carousel-button.prev {
    left: calc(50% - 347.5px); /* Adjust based on your main content width */
  }

  .carousel-button.next {
    right: calc(50% - 347px); /* Adjust based on your main content width */
  }

  .card-content {
    margin: 1rem;
  }
</style>
