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
    width: var(--nav-width);
    position: fixed;
    /* position: -webkit-sticky; */
    top: 0; /* required */
    z-index: 10;
    display: flex;
    justify-content: space-between;
    align-items: center;
    backdrop-filter: blur(0.5px); /* Adjust the blur radius as needed */
    background-color: #f5f5f4df;
    height: 24px;
    padding-top: 13px;
  }
  .nav-container {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
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
  .right-nav {
    margin-left: auto;
  }
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
