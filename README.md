# Diabetes-ML-Project
Training ML techniques (KNN, Random Forest, Pruned Tree, Gradient Boosting) on a small diabetes dataset, then applying it to a test dataset to compare performance metrics (accuracy, error, F1 score, ROC-AUC etc...) in diabetes prediction.

The aim of this project was to compare the performance of various supervised machine learning techniques in predicting diabetes in a small test dataset (282 women, 8 variables), having been trained on a small training dataset (250 women, 8 variables). Variables included:

1. Number of pregnancies [npreg]
2. Plasma glucose concentration in an oral glucose tolerance test [glu]
3. Diastolic blood pressure in mm/Hg [bp]
4. Triceps skin fold thickness in mm [skin]
5. Body mass index (weight in kg / (height in m)^2) [bmi]
6. Diabetes pedigree function (a feature that estimates an individual's likelihood of developing diabetes based on a range of information) [ped]
7. Age in years [age]
8. 'Yes' or 'No' for being diabetic [type]

The datasets were read in, [type] was converted to a factor [type_f] labelled 'Y' or 'N'. 
Ggplot2 was used to visualise the relationship between [bmi] and [glu], coloured by [type_f].
[npreg] was converted to a factor with levels '1', '2', '3'. '4'. '5'. '6 or more'.
A binary logistic regression model was fitted on the training data, with response variable [type_f] using the following covariates:
- [npreg_6_f]
- linear, quadratic and cubic functions of [age], [glu], and [bmi]
- [bp]
- [skin]
- [ped]
- [glu] * [bmi]

This model was simplified using backward elimination (following hierarchy/interaction rules) until only statistically significant variables remained. The final model was applied to the training data and used to predict diabetes (0.5 threshold for a type 'Y' classification), and a confusion matrix was presented. Performance metrics such as error, accuracy, sensitivity, specificity and precision were calculated for comparison.

The same process was carried out for a simpler binary logistic regression model (no quadratic/cubic functions or interaction terms). A function was written to calculate the F1 score for this simple binary logistic regression model.

Ggpairs from the GGally package was used to produce a matrix of scatter plots of the seven covariates, coloured by type_f.

Several ML models were trained with and applied to the diabetes datasets, including K-nearest neighbours (KNN), Gradient Boosting, Pruned Tree, and Random Forest. Performance metrics were calculated for all models and tabulated.

Receiver Operating Characteristic (ROC) curves and Area Under the Curve (AUC) measures were produced for the simpler binary logistic regression model and for the Gradient Boosting model.

All measures were compared and used to conclude which of these ML models performed the best in this scenario.
