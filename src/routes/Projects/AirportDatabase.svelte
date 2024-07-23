<script lang="ts">
  import { onMount } from "svelte";
  import admin_view from "$lib/assets/admin_view.png";
  import searchable_flights from "$lib/assets/searchable_flights_ui.png";

  interface ModalData {
    src: string;
    alt: string;
  }

  let activeModal: ModalData | null = null;

  function openModal(imageSrc: string, imageAlt: string): void {
    activeModal = { src: imageSrc, alt: imageAlt };
  }

  function closeModal(): void {
    activeModal = null;
  }

  function handleKeydown(event: KeyboardEvent): void {
    if (event.key === "Escape" && activeModal) {
      closeModal();
    }
  }
</script>

<div class="container">
  <div class="header">
    <h1>Airport Management System</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      With a friend, we built out a database system for the model problem of
      managing an airport. This involved first formally designing an appropriate
      data model, planning out what tables and permissions should be involved,
      generating realistic data for demonstrations, implementing the database
      and all the query logic, and finally wrapping it in a clean UI.
    </p>
  </div>

  <div class="content">
    <h2>Views</h2>
    <div class="image">
      <figure style="margin-bottom: 1rem;">
        <img
          src={admin_view}
          alt="Admin View"
          style="width:102%; max-width:102%; cursor: pointer;"
          on:click={() => openModal(admin_view, "Admin View")}
        />
        <figcaption>Admin View</figcaption>
      </figure>
    </div>
    <div class="text">
      <p>
        The project has three different views that can be logged into:
        administration, crew members, and passengers. Each view has a complete
        user interface for viewing the allowed information, such as upcoming
        flights as well as modifying the allowed information.
      </p>
      <p>
        For example, a passenger can see info about their own upcoming flights,
        as well as all flights that will be going into and out of the airports.
        They can then book flights, cancel flights, swap flights, or modify
        information about a flight such as the number of bags or their seat (if
        other seats are available). On the other hand a crew member can view
        their own schedules including information about what other crew are on
        the flights they are working, as well as what seats are full on those
        flights.
      </p>
      <p>
        All of the permissions are handled through SQL views to ensure no
        unintended data is available.
      </p>
    </div>

    <div class="section">
      <div class="text">
        <h2>Utility</h2>
        <p>
          Each view is fully functioning with the expected utility. The data
          model stores airlines, planes, terminals, destinations, flights, crew
          members, passengers, bags, and booking info. New users, passengers,
          and flights can be dynamically created and edited via the admin UI.
          Passengers may create and modify bookings, as well as their baggage
          info.
        </p>
        <p>
          To aid in usability, dynamic searching is done via dropdown menus that
          create dynamic SQL queries. This makes finding specific information
          like flights on a specific day simple. Furthermore, searches can be
          downloaded into an easily readable text format for logging and further
          analysis.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={searchable_flights}
            alt="Flight Search UI"
            style="width:105%; max-width:105%; cursor: pointer;"
            on:click={() => openModal(searchable_flights, "Flight Search UI")}
          />
          <figcaption>Flight Search UI</figcaption>
        </figure>
      </div>
    </div>

    <div class="text">
      <h2>How It Was Made</h2>
      <p>
        To build the final project, we used PostgreSQL via mariadb to handle all
        of the data. For the UI, we used PySide6 with components to implement a
        simple and easy to navigate design.
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

{#if activeModal}
  <div class="modal-overlay" on:click={closeModal}>
    <div class="modal-content" on:click|stopPropagation>
      <img src={activeModal.src} alt={activeModal.alt} />
      <button class="close-button" on:click={closeModal}>×</button>
    </div>
  </div>
{/if}

<style>
  /* ... your existing styles ... */

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

  .modal-content img {
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
