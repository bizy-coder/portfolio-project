<script>
  import confidence_scores from "$lib/assets/file4.png";
</script>

<div class="container">
  <div class="header">
    <h1>Adversarial NLP</h1>
  </div>

  <div class="overview">
    <h2>Overview</h2>
    <p>
      We investigated a <a
        href="https://arxiv.org/abs/2204.04636"
        target="_blank"
        rel="noopener noreferrer">state-of-the-art defense</a
      > against adversarial examples in NLP classifiers. Our research revealed an
      easy method to defeat the defense mechanism and demonstrated a general problem
      with NLP defenses, and concluded by working towards better generalized methods
      for evaluation.
    </p>
  </div>

  <div class="content">
    <div class="text">
      <h2>Background</h2>
      <p>
        While AI offers many potential benefits, one risk is our incomplete
        understanding of how it works. This has led to the discovery that small
        modifications to inputs can "trick" classifiers. Initially studied with
        images, this issue has extended to text classification and response
        systems used for tasks like spam classification and sentiment analysis.
      </p>
      <p>
        For text classification, these "attacks" work in a broad sense by
        changing words in an input until they find a change that seems to
        confuse the model. They then repeat this until the model is sufficiently
        confused it makes the wrong prediction. Some examples of this can be
        found near the bottom of this page.
      </p>
    </div>
    <div class="section" style="margin:0; padding:0"></div>
    <div class="section">
      <div class="text">
        <h2>Defense Mechanism Analysis</h2>
        <p>
          The published defense, aimed to determine whether an example was real
          or adversarial (tricking the model), by analyzing the distribution of
          the logits of the classifier. Upon further investigation, our research
          demonstrated that in practice this mostly functioned as a binary
          classifier based on model confidence (gaining less than 5% performance
          over this).
        </p>
        <p>
          As a result, the image on the left shows that the distribution of
          confidence in adversarial predictions vs clean predictions is nearly
          exactly dependent on confidence level.
        </p>
      </div>
      <div class="image">
        <figure>
          <img
            src={confidence_scores}
            alt="Confidence Scores for Clean and Adversarial Examples"
          />
          <figcaption>
            Confidence scores distribution for clean and adversarial examples
          </figcaption>
        </figure>
      </div>
    </div>

    <div class="section">
      <div class="text">
        <h2>Defeating the Defense</h2>
        <p>
          Using our understanding, we demonstrated how to trick the defense
          99.4% of the time without altering how a human would interpret the
          sentence, simply by swapping words. Our methods could trick the
          defense into misclassifying both real and adversarial examples.
        </p>
      </div>
      <div class="image">
        <div class="table-container">
          <table class="adversarial-detection-table">
            <caption>Adversarial Defense Confidence Dependence </caption>
            <thead>
              <tr>
                <th>Attack Confidence Threshold</th>
                <th>Defense Success Rate (%)</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>0.5</td>
                <td>93.0</td>
              </tr>
              <tr>
                <td>0.8</td>
                <td>73.6</td>
              </tr>
              <tr>
                <td>0.97</td>
                <td>0.05</td>
              </tr>
              <tr>
                <td>0.997</td>
                <td>0.00</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <h2>Example of NLP attacks + Defense</h2>
    <p>
      These examples demonstrate how the attack and defense work. Given an
      initial sample, words are changed to effect the model prediction. Here, we
      take the same sentence and change it in different ways. For each scenario
      we report the sentiment classification of the original model, as well as
      the prediction of the defense about whether the example was real or an
      adversarial example (AE).
    </p>
    <p>
      When the original model has a low confidence, the defense will assume it
      is an adversarial example, and when the confidence is high, it will assume
      it is valid. This is regardless of whether or not it was actually made
      adversarial
    </p>

    <div class="image">
      <div class="table-container">
        <table class="adversarial-detection-table">
          <caption>Adversarial Defense Confidence Dependence </caption>
          <thead>
            <tr>
              <th>Example Type</th>
              <th>Example Text</th>
              <th>Model Prediction</th>
              <th>Model Confidence</th>
              <th>Defense Prediction</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Original Example </td><td>
                I went there today! The cut was <b>[[terrible]]</b>! I have an
                awful experience. They lady that cut my hair was <b>[[nice]]</b>
                but she wanted to leave early so she made a disaster in my head!
              </td><td> negative </td><td> 100 </td> <td>Not Adversarial</td>
            </tr>
            <tr>
              <td>Low Confidence AE </td><td>
                I went there today! The cut was <b>[[monstrous]]</b>! I have an
                awful experience. They lady that cut my hair was
                <b>[[fantastic]]</b> but she wanted to leave early so she made a
                disaster in my head!
              </td><td> positive </td><td> 61 </td> <td>Adversarial</td></tr
            >
            <tr>
              <td>High Confidence AE </td><td>
                I went there today! The cut was <b>[[monstrous]]</b>! I have an
                awful experience. They lady that cut my hair was
                <b>[[marvelous]]</b> but she wanted to leave early so she made a
                disaster in my head!
              </td><td> positive </td><td> 90 </td> <td>Not Adversarial</td></tr
            >
            <tr>
              <td>Close Boundary non-AE </td><td>
                I went there today! The cut was <b>[[terrible]]</b>! I have an
                awful experience. They lady that cut my hair was
                <b>[[fantastic]]</b> but she wanted to leave early so she made a
                disaster in my head!
              </td><td> negative </td><td> 60 </td> <td>Adversarial</td></tr
            >
          </tbody>
        </table>
      </div>
    </div>

    <div class="text">
      <h2>Implications for Future Research</h2>
      <p>
        As it turns out, many different adversarial example defenses end up
        functioning the same. They are some complex model that effectively
        learns to classify based on confidence. Of course, this is problematic
        because a knowledgable attacker can simply require there attacked sample
        to have a confidence of 90% instead of 50%, and immediately defeat the
        model. In our testing, we even showed this is often not that much
        harder!
      </p>
      <p>
        To address this, we recommended further defemse research use two
        different types of attacks. First, they should use adaptive attacks that
        aim to simultaneously fool the model and prevent defense prediction from
        increasing. Second, they should use high confidence attacks that are
        normal attacks allowed to run until a high confidence.
      </p>
    </div>
    <div class="footer">
      <p>
        For more information, visit the project on <a
          href="https://github.com/bizy-coder/geolocation"
          target="_blank">GitHub</a
        >.
      </p>
    </div>
  </div>
  <!-- <div class="section"></div> -->
</div>

<style>
  .section {
    margin-bottom: 1.5rem;
  }

  .image {
    /* padding:2
            border: 1px;
            border-color: #990000; 
            border-collapse: collapse;
            border-style: solid; */
    margin: 1rem 0;
  }

  .table-container {
    /* margin: 1rem 0; */
    border-width: 100px;
    border-style: solid;
    border: black;
  }

  .adversarial-detection-table {
    width: 100%;
    border-collapse: collapse;
    /* font-size: 0.85rem; */
  }

  .adversarial-detection-table caption {
    font-weight: bold;
    margin-bottom: 0.5rem;
    text-align: center;
  }

  .adversarial-detection-table th,
  .adversarial-detection-table td {
    padding: 0.5rem;
    text-align: center;
    border: 1px solid #ccc;
  }

  .adversarial-detection-table th {
    background-color: #f5f5f5;
    font-weight: bold;
    font-size: 0.7rem;
    margin: 0px;
    padding: 5px;
  }

  .footer {
    margin-top: 1.5rem;
    font-size: 0.7rem;
    text-align: center;
  }

  img {
    max-width: 100%;
    height: auto;
    display: block;
    margin: 0 auto;
  }
</style>
