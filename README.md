# UK Accidents Severity
Classifying accidents on severity.

Source of data: https://www.kaggle.com/benoit72/uk-accidents-10-years-history-with-many-variables
 
- The dataset consists of three files:
  - Accident level information including the severity assigned for the accident overall.
  - Information on each vehicle involved in the accident.
  - Information on each casualty, per vehicle per accident.

- `combine.ipynb`: Aggregating casualty data down to the vehicle level, merging with vehicle data, aggregating down to accident level, and then combining with the accident.
- `explore.ipynb`: Exploratory analysis of the combined dataset.
- `predict.ipynb`: Using a decision tree to try and learn the accident severity classification, which revealed the precise rule used to determine accident severity.
- `predict_without_casualty.ipynb`: Removing some casualty related features to see how other features perform.

The decision tree in `predict.ipynb` performed perfectly since it learnt the precise rule which determined accident severity - it is equal to the severity of the most severely affected casualty. It managed to do this using `CasaultyFatal_sum_sum` and `CasaultySerious_sum_sum`, which are the total number of casaulties of those specific severity within the accident (summing with vehicles and across all vehicles involved in the accident). The tree then just checks if `CasaultyFatal_sum_sum > 0` and if `CasaultySerious_sum_sum > 0` to know which severity the accident will have been assigned.
