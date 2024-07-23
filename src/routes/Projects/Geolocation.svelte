<script>
  import geolocation_augmentations from "$lib/assets/geolocation_augmentations.png";
  import geolocation_predictions from "$lib/assets/geolocation_predictions.png";
  import geolocation_state_f1_scores from "$lib/assets/geolocation_state_f1_scores.png";
  import geolocation_top_k_accuracy from "$lib/assets/geolocation_top_k_accuracy.png";
</script>

<div class="container">
  <div class="header">
    <h1>US State Image Geolocation</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      This project explores the challenge of predicting the US state of origin
      for Google Maps images. Using advanced machine learning techniques, we
      developed a model capable of identifying the state based solely on visual
      cues from satellite imagery. This task presents unique challenges due to
      the subtle differences between states and the variety of landscapes within
      each state.
    </p>
  </div>

  <div class="content">
    <h2>Model Architecture</h2>
    <p>
      After extensive experimentation, we found that a Vision Transformer (ViT)
      outperformed traditional convolutional neural networks for this task. The
      ViT's ability to capture long-range dependencies in images proved crucial
      for identifying state-specific features across diverse landscapes.
    </p>
    <p>
      We experimented with multiple training approaches, including
      classification (predicting the state directly), regression (predicting
      latitude and longitude), and hybrid models that combined both tasks. To
      handle partial data where exact coordinates weren't available, we
      implemented custom loss functions that could train effectively on mixed
      data types.
    </p>
    <div class="section" style="margin:0;padding:0;"></div>
    <div class="section">
      <div class="text">
        <p>
          However, the most significant way to improve performance that we
          discovered was to add many augmentations. From a theoretical
          standpoint, every part of the image could be valuable to making the
          prediction. However, the model would generally only focus on a
          specific influence. To prevent this, augmentations including but not
          limited to: changing image angles, adding blur or color change
          effects, and blocking out significant portions of the image.
          Otherwise, the model did not learn to use the entire image resulting
          in significantly worse overall results, and notably mroe overfitting.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={geolocation_augmentations}
            alt="Geolocation Augmentations"
            style="width:105%; max-width:105%"
          />
          <figcaption>
            Examples of data augmentation techniques used during training
          </figcaption>
        </figure>
      </div>
    </div>

    <div class="section">
      <div class="image">
        <figure>
          <img
            src={geolocation_predictions}
            alt="Geolocation Predictions"
            style="width:100%; max-width:100%"
          />
          <figcaption>Example inputs and model predictions</figcaption>
        </figure>
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>Performance and Insights</h2>
        <p>
          Our model achieved an impressive accuracy of over 60% in correctly
          identifying the state from a single image. When allowed to provide its
          top 3 predictions, the accuracy increased to over 80%. This
          performance is particularly noteworthy given the challenging nature of
          the task and the visual similarities between many states.
        </p>
        <p>
          Interestingly, attempts to visualize the model's decision-making
          process using techniques like GradCAM did not reveal easily
          interpretable patterns. This suggests that the model learns to
          consider the entire image holistically rather than focusing on
          specific landmarks or features.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={geolocation_state_f1_scores}
            alt="State F1 Scores"
            style="width:105%; max-width:105%"
          />
          <figcaption>F1 scores for each US state</figcaption>
        </figure>
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>Dataset and Training</h2>
        <p>
          The model was trained on a dataset of 10,000 Google Maps images, with
          samples from various locations across each state. Remarkably, we found
          that the model performed well even when trained on just 500 examples
          per state, demonstrating its ability to generalize from limited data.
        </p>
        <p>
          We employed a range of data augmentation techniques to enhance the
          model's robustness and prevent overfitting. These included random
          rotations, flips, and color adjustments to simulate variations in
          lighting and seasonal changes.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={geolocation_top_k_accuracy}
            alt="Top-k Accuracy"
            style="width:105%; max-width:105%"
          />
          <figcaption>
            Model accuracy for different values of k in top-k predictions
          </figcaption>
        </figure>
      </div>
    </div>

    <div class="text">
      <h2>Technical Implementation</h2>
      <p>
        The project was built using the FastAI library, which provided a
        flexible framework for implementing custom model architectures and loss
        functions. We extended FastAI's capabilities by developing specialized
        heads for our multi-task learning approach and implementing custom loss
        functions to handle partial data.
      </p>
      <p>
        The Vision Transformer architecture was chosen for its superior
        performance in our initial experiments. We fine-tuned pre-trained ViT
        models, adapting them to our specific geolocation task through careful
        hyperparameter optimization and custom training routines.
      </p>
    </div>
  </div>

  <div class="footer">
    <p>
      For more information and access to the code, please visit the project
      repository on GitHub (link to be added).
    </p>
  </div>
</div>
