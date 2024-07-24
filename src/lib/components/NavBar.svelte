<script>
  export let width = "600px";

  // Navigation links data
  let navLinks = [
    { text: "Home", href: "/" },
    { text: "Projects", href: "Projects" },
    { text: "Work", href: "/#work" },
    { text: "Activities", href: "/#activities" },
  ];
</script>

<header>
  <nav style="--nav-width: {width};">
    <div class="nav-container">
      <ul class="left-nav">
        <li><p class="my-name">Benjamin Zydney</p></li>
      </ul>
      <ul class="right-nav">
        {#each navLinks as link}
          <li><a href={link.href}>{link.text}</a></li>
        {/each}
      </ul>
    </div>
  </nav>
</header>

<style>
  nav {
    background-color: #f1efe7;
    height: 2.5rem;
    padding-top: 1rem;
    width: var(--nav-width);
    max-width: 95%;
    position: fixed;
    top: 0;
    z-index: 10;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav-container {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  /* Add this new rule for the blur effect */
  nav::after {
    content: "";
    position: fixed;
    top: 2.75rem; /* Same as nav height */
    left: 0;
    right: 0;
    height: 1rem; /* Adjust this value to control the blur height */
    background: linear-gradient(
      to bottom,
      rgba(241, 239, 231, 0.7) 100%,
      rgba(241, 239, 231, 0.3) 100%
    );
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px); /* For Safari */
    z-index: 9; /* Just below the nav */
    pointer-events: none; /* Allows clicking through the blur */
  }
  .left-nav,
  .right-nav {
    list-style: none;
    padding: 0;
    display: flex;
    align-items: center;
  }
  .right-nav {
    gap: 0.3rem;
  }
  .right-nav li:not(:last-child)::after {
    content: "|";
    margin-left: 0.3rem;
  }
  /* .right-nav {
    margin-left: auto;
  } */
  li {
    margin: 0;
  }
  a,
  a:link,
  a:visited {
    font-size: small;
    font-family: ui-serif, Georgia, Cambria, "Times New Roman", Times, serif;
    font-weight: lighter;
    color: #919190;
    /* text-decoration: none; */
    line-height: 1.5;
    margin: 0;
    padding: 0;
    /* transition: transform 0.2s ease, font-weight 0.2s ease; Smooth transition */
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
  .my-name {
    font-size: small;
    font-family: ui-serif, Georgia, Cambria, "Times New Roman", Times, serif;
    font-weight: bold;
    color: #919190;
    text-decoration: none;
    line-height: 1.5;
    margin: 0;
    padding: 0;
  }
</style>
