# Machine Learning Analysis

### Machine learning model to analyze Kepler Exoplanet search results

The model uses pandas, matplotlib and sklearn libraries train_test_split, MinMaxScaler and KNeighborsClassifier. The model operates on the assumption that planets can be classified using measurements from the columns koi_fpflag_nt, koi_fpflag_ss, koi_fpflag_co and koi_fpflag_ec. Koi_pdisposition was used as the actual values column. Values in this column were encoded from "Candidate" and "False Positive" to 1, 0 with 1 representing true and 0 representing false. For an exoplanet listed as "Candidate", the Candidate column would reflect 1 for true and the False Positive column would reflect 0. 

Train test split was calculated based on these values for X and y with a random state shuffle of 25. X data was scaled using MinMaxScaler and transformed. Next, we used KNeighbors to calculate training, testing and total scores for each neighbor value of K. For this model, KNeighbors were chosen from a range of 1-15 with a step value of 3 resulting in K values of 1, 4, 7, 10 and 13. The total score (test score + train score) was calculated for each K value.

For this model, we found that the total scores remained the same for each K value. We also tested different ranges and step values for K with similar results for total score. Since the total score was the same for all K values, we assumed that the second K value (4) represented the point at which the model begins to stabilize. Using a K value of 4, the model is 98% accurate.