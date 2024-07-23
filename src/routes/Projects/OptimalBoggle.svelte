<script>
  import best_board from "$lib/assets/best_board_transparent.png";
  import hill_climb from "$lib/assets/transparent_background_board.gif";
</script>

<div class="container">
  <div class="header">
    <h1>Optimal Boggle Boards</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      Word Hunt/Boggle are word games where players find words in a grid of
      letters by connecting adjacent tiles, without reusing any tile in the same
      word. As a fan of Boggle, I became intrigued by the challenge of creating
      the optimal board, one that theoretically yields the highest possible
      score.
    </p>
  </div>

  <div class="content">
    <div class="section">
      <div class="text">
        <h2>Scoring Potential</h2>
        <p>
          In typical gameplay, players have about one minute to find words and
          accumulate points, often maxing out around 30,000 points on a good
          board. However, significantly higher scores are theoretically
          possible.
        </p>
        <p>
          Efficiently calculating these scores is rather challenging. Looking at
          all 300,000 words each iteration is quite slow. Instead, I build a
          trie out of the input words, and then recursively traverse the trie,
          while efficiently keeping track of visited tiles. This is then easily
          parallelized to search from all of the starting tiles simultaneously
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={best_board}
            alt="Best Boggle Board"
            style="width:105%; max-width:105%"
          />
          <figcaption>The highest scoring 4x4 Word Hunt board</figcaption>
        </figure>
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>Optimization</h2>
        <p>
          To determine the optimal Boggle board, I implemented a genetic
          algorithm for global search with hill climbing for local optimization.
          My initial approach used Simulated Annealing, but often times this
          still was failing to escape local minima. As a result, this Genetic
          Algorithm approach was chosen instead. This approach efficiently
          discovers high-scoring 4x4 boards and can approximate optimal
          configurations for other board sizes and shapes.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={hill_climb}
            alt="Hill Climb Animation"
            style="width:105%; max-width:105%"
          />
          <figcaption>Hill Climbing approach on a random board</figcaption>
        </figure>
      </div>
    </div>

    <div class="text">
      <h2>How It Was Made</h2>
      <p>
        The project was originally built from scratch in Python. The core
        searching features were all written in core Python. Matplotlib and
        Imageio were used for creating visualizations.
      </p>
      <p>
        More recently, the code has been rewritten in C++ providing about a ~15x
        speed improvement. This was done to allow searching for larger boards,
        and with the ultimate goal of finding the smallest board that contains
        every word in the scrabble dictionary.
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
