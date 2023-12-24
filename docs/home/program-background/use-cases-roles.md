# Supported Use Cases & Roles

## Use cases

The JATIC program is currently focused on developing AI T&E capabilities for computer vision (CV) classification and object detection tasks. The libraries and tools that the program are building are designed to be applicable across mission use cases that employ these types of AI algorithms. In particular, the primary mission use cases which we are focused on are:

1. Satellite imagery - CV Object Detection
1. UAV imagery - CV Object Detection
1. Autonomous driving - CV Object Detection
1. Medical imagery - CV Classification

These should not preclude application to other tasks, but serve as the primary missions that guide our development.

For the above missions, we are working with DoD mission-owners to apply our tools into their T&E workflows. For each of the above use cases, we select an open-source dataset which "represents" the mission to serve as our working target. Often, we use these datasets within our development and demos.

## Roles & personas

The libraries and tools developed within our program support a number of different types of users within the MLOps lifecycle. The primary roles that we are focused on are the following:

1. AI T&E engineer
1. Data scientist 
1. Data analyst
1. AI red teamer

For each of these roles, we have created have created concrete personas representing the role, including their backgrounds, preferences, and archetypal workflows. These personas can be found [TBD]. Below, we brovide an overview of each user type and their characteristics. 

### AI T&E engineer

- Measures performance of models within various settings and contexts
- Compares performance of models
- Verifies requirements satisfaction and validates evaluation results
- Performs quantitative evaluation of risks
- Explores potential unknown risks
- Develops summary report of findings
- Does not participate in model development

The AI T&E engineer, specifically within the DoD, is the primary role that we aim to support.

### Data scientist

- Exploratory data and model analysis
- Statistical analysis
- Model experimentation
- Feature engineering
- Model training and continuous fine-tuning
- Uses MLOps, end-to-end model pipelines

See Data Scientist and ML Engineer in [1], and Data Scientist in [2] and [3] for references and a general job description. 

### Data analyst

- Data visualization and analysis
- Statistical analysis of dataset properties
- Data set selection, curation, and validation
- Data preparation and cleaning

See Data Analyst in [3] and [4] for references and a general job description. 

### AI red teamer

- Perform adversarial assessments of AI models
- Perform threat analysis 
- Find system failure models
- Build proxy models to approximate real model performance
- Often possess limited model information

## References

1. [AWS Whitepapers ML Roles](https://docs.aws.amazon.com/whitepapers/latest/build-secure-enterprise-ml-platform/personas-for-an-ml-platform.html)
1. [Red Hat ML Roles](https://cloud.redhat.com/blog/your-guide-to-the-red-hat-data-science-model-lifecycle)
1. [Domino ML Roles](https://www.dominodatalab.com/blog/7-roles-in-mlops)
1. [AWS Well-Architected ML Roles](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mloe-04.html)