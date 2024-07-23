<script>
  // Import images if needed
  // import spanning_tree from "$lib/assets/spanning_tree.png";
  // import heuristic_comparison from "$lib/assets/heuristic_comparison.gif";
</script>

<div class="container">
  <div class="header">
    <h1>Maximum Leaf Spanning Trees</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      The Maximum Leaf Spanning Tree problem challenges us to find a subset of
      edges in a given graph that forms a spanning tree with the maximum number
      of leaf nodes. As an NP-hard problem, it requires innovative approaches
      beyond traditional algorithms. Our project, developed as part of Penn
      State's Graduate Algorithm course, introduces novel heuristics and
      transformations that outperform existing methods in both effectiveness and
      optimality proofs.
    </p>
  </div>

  <div class="content">
    <div class="section">
      <div class="text">
        <h2>The Challenge</h2>
        <p>
          With approximately 40 students tasked to implement the best approach
          possible, common solutions relied on optimizing existing approximation
          algorithms with worst-case guarantees. However, these methods often
          fell short in practical applications, performing relatively poorly
          compared to optimal solutions.
        </p>
        <p>
          Our challenge was twofold: develop a more effective heuristic approach
          and find a way to prove optimality for as many instances as possible,
          something no other team had achieved.
        </p>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={spanning_tree}
            alt="Maximum Leaf Spanning Tree"
            style="width:105%; max-width:105%"
          />
          <figcaption>Visualization of a Maximum Leaf Spanning Tree</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>Our Solution</h2>
        <p>We developed two key approaches to tackle this problem:</p>
        <ol>
          <li>
            <strong>Novel Heuristic Approach:</strong> We created a heuristic that
            repeatedly chooses edges based on their "centrality", quantified by the
            distance to all remaining untouched vertices. Extensive testing showed
            this method significantly outperformed existing approximation approaches.
          </li>
          <li>
            <strong>Partial Reduction to 3-SAT:</strong> We developed a novel (partial)
            reduction of the problem to a version of the 3-SAT problem. This allowed
            us to employ state-of-the-art 3-SAT solvers, enabling us to find optimal
            solutions and provide proofs of optimality for about 90% of the problem
            instances.
          </li>
        </ol>
      </div>
      <div class="image">
        <!-- Add an image here if available -->
        <!-- <figure>
          <img
            src={heuristic_comparison}
            alt="Heuristic Performance Comparison"
            style="width:105%; max-width:105%"
          />
          <figcaption>Performance comparison of our heuristic vs. traditional approaches</figcaption>
        </figure> -->
      </div>
    </div>

    <div class="text">
      <h2>Generating Challenging Test Cases</h2>
      <p>
        As a final part of the project, we developed a method to generate hard
        test cases:
      </p>
      <ol>
        <li>Generate random trees</li>
        <li>
          Strategically add edges to "obfuscate" the original tree without
          increasing the potential maximum leaf spanning tree
        </li>
        <li>
          Test difficulty using our heuristics and knowledge of the optimal
          solution
        </li>
      </ol>
      <p>
        This method resulted in test cases demonstrating the largest average gap
        from optimal among all submitted cases, effectively challenging other
        teams' solutions.
      </p>
    </div>

    <div class="text">
      <h2>Results and Impact</h2>
      <p>
        The combination of our heuristic approach and 3-SAT reduction method
        yielded impressive results:
      </p>
      <ul>
        <li>
          Solved all but 3 of over 120 test cases at least as well as any other
          team
        </li>
        <li>Our heuristic approach alone outperformed the next best method</li>
        <li>
          Provided proofs of optimality for ~90% of instances, a unique
          achievement in the class
        </li>
      </ul>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information and to explore the code, visit the project on
      <a
        href="https://github.com/bizy-coder/MaxLeafSpanningTree"
        target="_blank">GitHub</a
      >.
    </p>
  </div>
</div>
