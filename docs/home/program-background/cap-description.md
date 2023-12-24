# Capability Descripition

## Introduction

This document provides a technical overview of the JATIC Capability, focusing on the MVP to be developed in FY23.

## JATIC T&E Tools Vision

Develop AI T&E tools that are widely adopted by DoD programs to increase the rigor of their missions and by the open-source community

## Scope

For this MVP, JATIC aims to develop T&E capabilities to test AI/ML models for Computer Vision (CV) classification and object detection (OD).

While other AI modalities besides CV, such as autonomous agents and natural language processing also require T&E capabilities, they are out of scope for the current JATIC MVP.

CV classification and object detection was chosen as the AI modality for JATIC's MVP due to its wide use across the DoD in many operational contexts. CV models, often of very similar underlying architectures, are used across diverse tasks such as automatic target recognition, satellite imagery classification, medical imagery diagnosis, and object detection on UAVs, UUVs, and autonomous vehicles. Thus, T&E capabilities which support CV classification and object detection models may have broad applicability across the Department. Future AI modalities (e.g. natural language processing, full motion video, image segmentation, etc.) will be addressed in future capabilities releases of JATIC. However, the ordering and priority of each of these modalities is yet to be firmly determined and will evolve as CDAO T&E comes to better understand the prevalence and demand for T&E capabilities within each one of these areas.

While other areas of T&E, such as systems integration, human-machine, and operational T&E are complex issues with capabilities gaps, they are out of scope for JATIC.

Other areas of testing, such as systems integration testing, are far more difficult to develop generalizable T&E capabilities for. For example, while the same T&E software may be able to test a CV OD model for radiology and a CV OD model for vehicle detection on UAVs, the required systems integration testing for these two capabilities looks completely different. Thus, we believe that capabilities for systems integration, human system interaction, and operational testing should be left to individual organizations, agencies, and services to develop, who have the best knowledge about their operational mission and systems.

While operational monitoring of AI models and synthetic data generation are capabilities areas which are critical for AI/ML, they are out of scope for JATIC. This is because there are other programs within the CDAO which will address these capability gaps.

## Problem statement

There is widespread interest throughout the DoD for enterprise-level T&E capabilities to address the novel challenges posed by the T&E of AI. While many T&E capabilities have been developed by previous DoD AI Programs to meet the specific needs of those programs, their usage and distribution throughout the Department has been limited by several key factors, including:

1. Lack of capabilities for advanced AI T&E functions, such as robustness testing.
2. Lack of maturity, scalability, reproducibility, ease of use, or cyber-hardening of capabilities.
3. Difficulty deploying and using capabilities within DoD environments.
4. Difficulty using capabilities within ML pipelines and technology stacks.
5. Difficulty using capabilities in an integrated T&E pipeline, as each individual capability often requires custom model formats or data wrangling.
6. Inability for capabilities to evolve with developments in AI research.

These limitations, in addition to other factors, such as a lack of common standards and best practices for AI T&E, have inhibited the ability for DoD AI programs to perform comprehensive T&E of their AI models.

A further discussion of previous AI T&E capabilities can be found in JATIC Design Principles.

In addition previous capabilities were also greatly limited by the T&E functions that they enabled users to perform and were primarily limited to producing summary metrics of the performance of an AI model over an entire dataset. With only these functions it is difficult to understand the functioning of an AI model in operation.

It is not clear that a test dataset is well representative of an operational dataset, or that there are no biases in the test dataset. Even if an AI model does well overall across a test dataset, that does not indicate that it is free of biases or performance variations across the subclasses. It also does not indicate that it is robust to operationally realistic perturbations or adversarial attacks. Finally, understanding the overall performance of a model does not provide sufficient intuition for what features a model finds important or what criteria it is using to make its decision. Possessing these additional capabilities and more greatly strengthens the ability for a tester or analyst to understand the performance of an AI model.

## AI T&E Functionality

Within its minimum viable product (MVP), JATIC seeks to develop T&E capabilities within the following dimensions of AI T&E:

### Dataset Analysis

Dataset analysis capabilities allow T&E stakeholders to understand held out T&E datasets, including their quality and similarity to operational data. This dimension is focused on assessing properties of a dataset that are independent of a particular AI model under test. Example functionalities include (but are not limited to) the computation of:

- Dataset quality (e.g., label errors, missing data)
- Dataset sufficiency for a given test (e.g., number of samples, variation)
- Biases, outliers, and anomalies in the dataset, which may be naturally occurring or intentionally inserted (i.e., data poisoning)
- Comparison of two datasets (e.g., divergence of dataset distributions)

### Model Performance

Model performance capabilities allow T&E stakeholders to assess how well an AI model performs on a labeled dataset and across its population subclasses. Example functionalities include (but are not limited to):

- A comprehensive set of well-established CV metrics (e.g., precision, recall, mean average precision)
- Metrics to assess probability calibration, i.e., the reliability of the model's measure of predictive uncertainty (e.g., expected calibration error, entropy, reliability diagrams)
- Metrics to assess fairness and bias in model output across the test dataset (e.g., statistical parity)

In addition to pre-defined metrics, capabilities will support the creation of custom, user-defined metrics.

### Model Analysis

Model analysis capabilities expand upon the model performance dimension by allowing T&E stakeholders to gain a deeper understanding of a model's capabilities and limitations by uncovering hidden trends, patterns, or insights across the input space. Example functionalities include (but are not limited to) algorithms that:

- Detect trends in model performance across the entire dataset, such as distinct types of model errors
- Identify clusters of the model input space based on model predictions, feature values, network activations, etc.
- Identify potentially mislabeled ground truth data based on sets of model predictions
- Determine under-tested or high-value regions of the input space (for the model under test) to inform future test data collection or labeling

### Natural Robustness

Natural robustness capabilities enable T&E stakeholders to determine how natural corruptions in data can impact model performance. These corruptions emulate realistic noise that may be encountered within the operational deployment environment. Example corruptions include (but are not limited to):

- Pre-sensor, environmental or physical corruptions (e.g., fog, snow, rain, changes in target shape or dimensions)
- Sensory corruptions (e.g., out-of-focus, glare, blur)
- Post-sensor, in-silico corruptions (e.g., Gaussian noise, digital compression)

Capabilities for creating these corruptions may leverage synthetic data generation techniques. Capabilities will provide users with the ability to control the severity level of the corruption, so that performance can be reported as a function of severity level and T&E stakeholders can use these results to set or assess requirements on performance and robustness.

### Adversarial Robustness

Adversarial robustness capabilities enable T&E stakeholders to assess how adversarial corruptions on data inputs may impact model performance. The primary focus of this dimension will be on evasion-style attacks (i.e., attacks in which the adversary aims to manipulate the input data to produce an error in the model output, often covertly). Example types of attack methods include (but are not limited to):

- White-box and black-box methods
- Mathematical (e.g., Lp norm-constrained) and physically realizable (e.g., patch) attacks
- Empirical and certified attacks

In addition to pre-defined attacks, capabilities will provide lower-level building blocks to enable users to create their own adaptive attacks that can be customized to the specific AI model under test. Capabilities will provide users with the ability to control the attack severity and assess performance given varying assumptions on adversary knowledge and adversary capabilities.

### Model Cards, Data Cards, and T&E Reports

Model cards, data cards, and T&E reports provide summarized information about a model or datasets performance for end-user consumption. 

Example functionalities include:

- Ingestion of metrics and results from other tools
- Machine readable formats, compatible with experiment tracking and dashboarding tools
- Human readable formats, e.g., powerpoint report generation

## AI Assurance Toolbox

Most of the software developed within the JATIC program in FY23 will fall within the **AI Assurance Toolbox**.

This toolbox will be a set of python libraries, mutually compatable, built on a set of shared design principles, with a narrowly scoped set of functionality specific to AI T&E.

Tools within the AI Assurance Toolbox will generally adhere to the following principles:

- Will be usable as independent but mutually compatabible python libraries
- Will prefer a narrow scope of functionality constrained to AI T&E, making use of existing open-source solutions for common ML tasks like data loading, experiment tracking, visualization, model inference, etc.
- Will implement open-source standard APIs for models, datasets, etc.
- Will build upon existing open-source libraries (especially when the open-source components are widely used and recognized), increasing their maturity, compatibility, or relevancy for DoD usage
- Will (where appropriate) publically release or open-source capabilities
- Will be designed to enable straightforward contributions from developers in the community
- Will be designed to enable continual evolution with the state-of-the-art in AI T&E and updates in ML technologies
- Will allow users to add functions (e.g., custom metrics, perturbations, adversarial attacks) in an extensible way
- Will be lightweight and straightforward to run on a wide range of deployment environments, including all major operating systems, cloud deployments, etc.
- Will be comprhensively supported with examples, tutorials, and documentation

By limiting the software form factor to python libraries, a narrow scope of functionality, and heavy re-use of open-source, this toolbox will be sufficiently flexible to be easily usable within many different T&E workflows, ML technology stacks, and compute environments. For instance, individual libraries within the AI Assurance Toolbox will be usable independently within Jupyter Notebooks to enable quick model testing and metrics visualization (e.g., gradio, streamlit), and also within production-level ML pipelines - leveraging features such as test automation, experiment tracking, and visualization dashboards - to enable powerful new insights into model performance.

In addition, while JATIC is primarily focused on supporting T&E of models after training, the libraries within the AI Assurance Toolbox will be applicable to many other phases of the AI lifecycle, such as model development or post-deployment monitoring.

## AI T&E platform

We noted above how libraries within the AI Assurance Toolbox are sufficiently flexible to be used within many AI/ML platforms, given their lightweight form factor and narrow scope. However, some common MLOp capabilities such as automation, tracking, and visualization are critical components for any AI T&E pipeline. By not providing this functionality in the AI Assurance Toolbox (as to not duplicate effort which exists in many MLOps platforms), it becomes very hard for users without an existing platform or pipeline (which we call "platform-free" users in the Design Principles) to use these tools to their full potential - the libraries will seem fragmented and disconnected.

For these users, the AI Assurance Toolbox may be delivered altogether, bundled together with open-source, industry-standard tools for workflow automation, experiment tracking, object storage, visualization, etc. This will provide a comprehensive and opinionated platform for AI T&E, which may either be adopted wholesale or used as a reference architecture. We call this platform the **AI T&E Platform**. 

The AI T&E Platform will be deployable to a Kubernetes cluster on commercial cloud (AWS, Azure primary targets) or on-prem. Additionally, it will be deployable to local machines as a set of dockerized micro-services. It will enable the use of infrastructure as code to quickly be deployable to a diverse set of envrionments.

## Areas of focus

JATIC is a program that aims to develop mature software which can be leveraged widely across the DoD. The following are the areas of focus within JATIC work.

### Integrations

Four types of integration are critical:
1. Easy deployments of tools into varied DoD environments
2. Easy integration of tools into varied MLOps platforms and stacks
3. Easy integration of tools with common ML model and dataset formats
4. Integration of tools with each other

We hope that the python library modality of tools within the AI Assurance Toolbox makes 1. reasonably easy.

For 2., some example ML technology categories and instances to that we are considering compatibility with include:

- ML frameworks: PyTorch, TensorFlow, HuggingFace
- ML pipelines: Databricks, SageMaker
- Compute engines: Kubernetes, Spark, Ray
- Orchestrators: Airflow, Kubeflow, Pachyderm
- Scalability frameworks: PyTorch Lightning, Horovod

Integration into these technologies, in may cases, is not necessarily deep. Since JATIC software is designed as python libraries, integration with a given technology may simply mean that they can easily be made to work together within python code, because of their expected formats, interface design, etc.

To enable much of this integration within 2., 3., and 4., the JATIC team will develop a set of standardized protocols for models, datasets, metrics, and transformations. These protocols will make use of structural subtyping within python and will be heavily inspired by existing protocols within HuggingFace, Pytorch, and TensorFlow for maximimum compatability. In addition, our development shall place heavy emphasis on diligent API design in order to enable straightforward compatibility with a wide range of technologies.

To enable 4., we will ensure consistent protocol expectations and version support across all of our tools.

### Productization

- Increase code quality, polish, speed, stability, scalability, and security of code. 
- Resolve technical debt, hacked solutions, etc.

### Documentation, tutorials, and usability

- Increase quality and quantity of useful end-user documentation.
- Create detailed tutorials and example workflows, especially aimed at those who may be less familiar with AI development.
- Increase user enjoyment out of software
- Increase usability of software.

## Intellectual Property

Government will have full ability to access, re-distribute, and modify code.

Developing vendors will retain the right to license their code with an open-source license and release it publicly (subject to some constraints on government exclusive features).
