# Sampling for Machine Learning -- Train-Test Splits

## Objective
I compared naive and stratified train-test splits and fixed data leakage to show how sample design changes a model evaluation.

## Methodology
- I loaded the Titanic dataset of 891 passengers with pandas and used survival as the target.
- I measured the survival rate overall and by passenger class and plotted both.
- I split the data with a naive random split and with a stratified split and compared the survival rate and the class shares in each half.
- I stratified on passenger class and survival together and checked both again.
- I showed data leakage by fitting a StandardScaler on all the rows before splitting and fixed it by splitting first and fitting on the training rows only.
- I fixed the same leak in a SimpleImputer step for missing ages.
- I wrote a function, split_by_share(), that splits a table by a test share and a seed, and I checked it against the lab's own split.

## Key Findings
- Survival depended on passenger class, with 1st class passengers surviving at a much higher rate than 3rd class passengers.
- The naive split left the test set survival rate further from the overall rate than the stratified split did.
- Stratifying on survival kept the survival rate the same in both halves but did not guarantee the class shares, which stayed close but not exact.
- Fitting the scaler on all the rows let the test rows change the numbers used on the training rows, and fitting on the training rows only removed that leak.
- The imputer had the same leak and the same fix, so the test rows were filled in with a number computed without them.
- My split_by_share() function reproduced the lab's own split.
