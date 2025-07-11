# FDA-Model-Search

FDA_Model_Search
FDA_Model_Search is a MATLAB function that systematically evaluates all possible n feature combinations from a dataset, fits a Fisher Discriminant Analysis (FDA, equivalent to LDA for two classes) model to each, and identifies those models that meet or exceed a user-specified AUROC (Area Under the Receiver Operating Characteristic Curve) threshold. This is particularly useful for feature selection and model performance screening in classification tasks.

Requirements
MATLAB (tested with R2018b or later recommended)

FDA_CV_AUROC function (must be available in your path; provides cross-validation and AUROC calculation)

Notes
The function only supports binary classification.

The input data must be in MATLAB table format.

The script is computationally intensive for datasets with a large number of features.

Custom Function: FDA_CV_AUROC
This script requires a custom function FDA_CV_AUROC for cross-validation and AUROC calculation. Please ensure this function is available in your MATLAB path. Example signature:

matlab
function [mean_auc, std_auc, mean_acc, std_acc, cv_acc] = FDA_CV_AUROC(X, y)
% X: table of predictors
% y: vector of class labels
% Returns cross-validated AUROC and accuracy metrics
License
This repository is released under the MIT License. See LICENSE for details.
