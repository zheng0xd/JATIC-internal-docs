# AI T&E Areas

<!--This section is probably no longer needed. This description should now be fulfilled by the documentation of the particular tools-->

Within its minimum viable product (MVP), JATIC seeks to develop T&E capabilities within the following dimensions of AI T&E:

## Dataset Analysis

Dataset analysis capabilities allow T&E stakeholders to understand held out T&E datasets, including their quality and similarity to operational data. This dimension is focused on assessing properties of a dataset that are independent of a particular AI model under test. Example functionalities include (but are not limited to) the computation of:

- Dataset quality (e.g., label errors, missing data)
- Dataset sufficiency for a given test (e.g., number of samples, variation)
- Biases, outliers, and anomalies in the dataset, which may be naturally occurring or intentionally inserted (i.e., data poisoning)
- Comparison of two datasets (e.g., divergence of dataset distributions)

## Model Performance

Model performance capabilities allow T&E stakeholders to assess how well an AI model performs on a labeled dataset and across its population subclasses. Example functionalities include (but are not limited to):

- A comprehensive set of well-established CV metrics (e.g., precision, recall, mean average precision)
- Metrics to assess probability calibration, i.e., the reliability of the model's measure of predictive uncertainty (e.g., expected calibration error, entropy, reliability diagrams)
- Metrics to assess fairness and bias in model output across the test dataset (e.g., statistical parity)

In addition to pre-defined metrics, capabilities will support the creation of custom, user-defined metrics.

## Model Analysis

Model analysis capabilities expand upon the model performance dimension by allowing T&E stakeholders to gain a deeper understanding of a model's capabilities and limitations by uncovering hidden trends, patterns, or insights across the input space. Example functionalities include (but are not limited to) algorithms that:

- Detect trends in model performance across the entire dataset, such as distinct types of model errors
- Identify clusters of the model input space based on model predictions, feature values, network activations, etc.
- Identify potentially mislabeled ground truth data based on sets of model predictions
- Determine under-tested or high-value regions of the input space (for the model under test) to inform future test data collection or labeling

## Natural Robustness

Natural robustness capabilities enable T&E stakeholders to determine how natural corruptions in data can impact model performance. These corruptions emulate realistic noise that may be encountered within the operational deployment environment. Example corruptions include (but are not limited to):

- Pre-sensor, environmental or physical corruptions (e.g., fog, snow, rain, changes in target shape or dimensions)
- Sensory corruptions (e.g., out-of-focus, glare, blur)
- Post-sensor, in-silico corruptions (e.g., Gaussian noise, digital compression)

Capabilities for creating these corruptions may leverage synthetic data generation techniques. Capabilities will provide users with the ability to control the severity level of the corruption, so that performance can be reported as a function of severity level and T&E stakeholders can use these results to set or assess requirements on performance and robustness.

## Adversarial Robustness

Adversarial robustness capabilities enable T&E stakeholders to assess how adversarial corruptions on data inputs may impact model performance. The primary focus of this dimension will be on evasion-style attacks (i.e., attacks in which the adversary aims to manipulate the input data to produce an error in the model output, often covertly). Example types of attack methods include (but are not limited to):

- White-box and black-box methods
- Mathematical (e.g., Lp norm-constrained) and physically realizable (e.g., patch) attacks
- Empirical and certified attacks

In addition to pre-defined attacks, capabilities will provide lower-level building blocks to enable users to create their own adaptive attacks that can be customized to the specific AI model under test. Capabilities will provide users with the ability to control the attack severity and assess performance given varying assumptions on adversary knowledge and adversary capabilities.

## Model Cards, Data Cards, and T&E Reports

Model cards, data cards, and T&E reports provide summarized information about a model or datasets performance for end-user consumption. 

Example functionalities include:

- Ingestion of metrics and results from other tools
- Machine readable formats, compatible with experiment tracking and dashboarding tools
- Human readable formats, e.g., powerpoint report generation
