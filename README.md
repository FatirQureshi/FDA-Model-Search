# FDA-Model-Search

FDA_Model_Search
FDA_Model_Search is a MATLAB function that systematically evaluates all possible n feature combinations from a dataset, fits a Fisher Discriminant Analysis (FDA, equivalent to LDA for two classes) model to each, and identifies those models that meet or exceed a user-specified AUROC (Area Under the Receiver Operating Characteristic Curve) threshold. This is particularly useful for feature selection and model performance screening in classification tasks.

Features
Exhaustive Search: Evaluates all n number of feature combinations from the input data.

FDA/LDA Modeling: Fits an FDA (LDA) model to each feature subset.

AUROC Screening: Computes the AUROC for each model and retains only those meeting the minimum threshold.

Cross-Validation: Reports cross-validated accuracy for each selected model (requires a custom function).

Customizable: User specifies the AUROC threshold.

Function Signature
matlab
all_auc = FDA_Model_Search(trans_table, labels, auc_thresh)
Inputs
Name	Type	Description
trans_table	Table	Predictor variables (observations x features)
labels	Vector or Table	Class labels (column vector or single-column table)
auc_thresh	Numeric Scalar	Minimum AUROC threshold for model selection
Output
Name	Type	Description
all_auc	Matrix	Each row: [feature indices, AUROC, CV accuracy] for selected models
Usage Example
matlab
% Example usage:
% trans_table: a MATLAB table with predictor variables
% labels: a column vector or table with class labels
% auc_thresh: minimum AUROC threshold (e.g., 0.85)

all_auc = FDA_Model_Search(trans_table, labels, 0.85);
Output Structure
Each row of all_auc contains:

Indices of the 4 selected features

AUROC of the model

Cross-validated accuracy (using FDA_CV_AUROC)

Feature 1	Feature 2	Feature 3	Feature 4	AUROC	CV Accuracy
...	...	...	...	...	...
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
