<script>
  // Sample data for posts
  let posts = [
    { title: 'Astro 4.9 Update', description: 'Astro 4.9 Update adds container api support and much more!' }
  ];
</script>

<div>
  {#each posts as post}
    <div>
      <h3>{post.title}</h3>
      <p>{post.description}</p>
    </div>
  {/each}
</div>

<style>
  div {
    margin-bottom: 1rem;
  }
  h3 {
    margin: 0.5rem 0;
  }
  p {
    margin: 0;
  }
</style>
