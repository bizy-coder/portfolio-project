<script>
  // Sample data for projects
  let projects = [
    { 
		title: 'This Website', 
		description: 'An elegant portfolio website to display my projects, built with Svelte.' 
	},
	{
		title: "space filler",
		description:`Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc pulvinar turpis eget nulla finibus, quis luctus erat dignissim. In malesuada sagittis ante sed suscipit. Vestibulum quis nunc turpis. Sed nibh odio, aliquam in lacus et, posuere accumsan massa. Donec nec convallis nunc. Vivamus et purus non ipsum molestie commodo. Mauris lorem nisl, vestibulum nec lacinia ac, sollicitudin eget risus. Praesent pulvinar sed augue quis maximus. In nec eros augue. Nunc risus dui, porta nec lacus eu, vestibulum pellentesque est. Quisque sagittis massa sem. Vivamus laoreet eu velit non feugiat. Maecenas hendrerit sodales justo eget maximus.

Aliquam at nisi nec risus faucibus ullamcorper. Quisque ultricies quam at porttitor consequat. Donec eu dapibus ipsum. Ut vulputate convallis arcu sed facilisis. Quisque ac pellentesque lacus, eu pellentesque elit. Integer venenatis aliquet risus non pretium. Ut eu leo ac nisi scelerisque efficitur. Curabitur lacinia tortor in elementum mollis. Praesent tellus sem, auctor luctus metus ut, convallis imperdiet quam. Cras sodales quis justo vitae eleifend. Fusce a imperdiet nunc. Donec ut dui odio. Quisque nisi velit, laoreet eu sodales vel, imperdiet ac nulla. Suspendisse potenti. Donec id tincidunt elit. Cras convallis vulputate pellentesque.

Aliquam erat volutpat. Nam lacinia scelerisque est, a facilisis lacus pellentesque eget. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce molestie lorem volutpat quam bibendum, ornare sodales arcu posuere. Duis mattis luctus consequat. Sed vitae pulvinar nunc. Integer commodo ante ut placerat molestie. Curabitur a vestibulum nisl. Etiam placerat augue tellus, vel tincidunt erat porta id. Quisque mattis tellus a aliquam mollis. Mauris tincidunt ipsum ac lacus sodales, sed semper nunc hendrerit. Mauris congue, turpis at lacinia vulputate, lectus lectus egestas purus, eget rutrum arcu ante in dolor. Duis consequat molestie commodo.

Mauris ultrices urna vitae aliquam dapibus. Praesent arcu neque, faucibus consectetur ultrices vel, fringilla non elit. Fusce et lorem id turpis porta eleifend. Suspendisse semper vitae urna vitae pulvinar. Aenean tempor, quam vitae porttitor egestas, ipsum erat porttitor urna, nec pulvinar neque tortor vel tortor. Aliquam faucibus rhoncus eros. Donec efficitur ex lacus, quis fringilla arcu consectetur in. Proin diam nunc, sagittis sit amet massa nec, blandit faucibus ante. Vivamus ornare ipsum at viverra sodales. Interdum et malesuada fames ac ante ipsum primis in faucibus. Integer posuere tellus ligula, in tristique nisl pretium eu. Morbi ut odio ac ipsum vehicula suscipit.

Fusce et malesuada ex. Duis elementum neque in diam imperdiet tempus. In hac habitasse platea dictumst. Proin volutpat lacus ipsum, id aliquam diam auctor vel. Sed tempor eleifend congue. Suspendisse tincidunt ipsum sit amet finibus consectetur. Fusce a dignissim nunc. Vivamus dictum elit nec mauris tempor malesuada. Ut ultrices quam commodo eros tincidunt sodales. Aliquam vitae enim odio. Nullam sollicitudin consectetur vulputate. Mauris et volutpat tortor. Integer quis magna vulputate, porttitor risus et, commodo eros. Phasellus non pellentesque ipsum, sed dictum dui. Aliquam non tempus dolor.`
	}
  ];
</script>

<div>
  {#each projects as project}
    <div>
      <h3>{project.title}</h3>
      <p>{project.description}</p>
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
