# compute_node_clustering

Author : Adithya Vikram Raj Garoju 📧

Date: 10th May 2022 📅

  Steps:
  1. ELK logs are transformed accordingly to accomodate more data comparatively in lesser rows and columns. 
      *   Segregated data Metric wise
      *   Merged them based on hostname inspite of timestamp


  2. Based on Correlation (pearson coefficient) if any columns correlation factor is greater than 0.95 they can be excluded.

  3. Performed following clustering techniques:
        *   Gausian Mixture Model
            - chosen n_components based on AIC and BIC trend.
        *   DBSCAN
            - started out with randome eps and min_samples.
        *   Isolation Forest
            - Chosen 5% contamination factor.

  4. The better fit algorithm for current scenario among the above would be Isolation Forest classifier .
      *  Due to comparitively low hyper-parameters to choose.
      * Isolation Forest stands out when compared to both DBSCAN and GMM, since both of them follow Expectation Maximization Approach.
      * Additionally we are not opting to segement given hosts to various classes we primarily want to deal with anomolies, we can skip to choose components or min_samples instead focusing on contamination factor.
      * The data traffic is expected to receive for every 15 mins for finding host outliers.
      * Isolation Forest would be a good fit for online model deployement due to its model persistence and it doesnt need to train every time unlike DBSCAN. We can predict new instances and recommend outliers.
      * Also GMM would do but we need to choose n_components all the time which is not relevant at this point of time.
      * We can utilize the warm_start param and update our model with new set of log data to prevent our model from getting stale. 
      (Also catching up with moore's law 😉)



[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1EUxNKGWhHbPNOtsWExg5-TmDt78m0R5N?usp=sharing)
