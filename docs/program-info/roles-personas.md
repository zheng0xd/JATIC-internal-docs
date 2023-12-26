# Supported Roles & Personas

The products developed within our program support a number of different types of users within the MLOps lifecycle. The primary roles that we are focused on are the following:

1. AI T&E engineer
1. Data scientist 
1. AI red teamer

For each of these roles, we have created have created concrete personas representing the role, including their backgrounds, preferences, and archetypal workflows. These personas can be found [TBD]. 

Below, we brovide an overview of each user type and their characteristics. 

## Supported roles

### AI T&E engineer

- Measures performance of models within various settings and contexts
- Compares performance of models
- Validates testing data with operational conditions
- Verifies requirements satisfaction and validates evaluation results
- Performs quantitative evaluation of risks
- Explores potential unknown risks
- Develops summary report of findings
- Does not participate in model development
- Often operates as a third-party from both developers or customers

!!! note

    The AI T&E engineer, specifically within the DoD, is the primary role that we aim to support.

### Data scientist

- Performs exploratory data and model analysis
- Performs statistical analysis over data
- Performs feature engineering
- Performs model experimentation, training, and fine-tuning
- Uses MLOps pipelines and platforms
- Calibrates and re-trains models after drift

!!! note

    The data scientist is the secondary role that we aim to support after the AI T&E engineer. 
    
    Because testing is performed continually during throughout model experimentation and training, many products built specifically for T&E may be relevant. 

### AI red teamer

- Performs threat analysis 
- Performs adversarial assessments of AI models
- Finds system failure models
- Builds proxy models to approximate real model performance
- Possess limited model information

!!! note

    For most products, the AI red teamer is a secondary user group. However, it is an important user group for our adversarial AI capabilities.

## References

1. [AWS - Personas for an ML platform](https://docs.aws.amazon.com/whitepapers/latest/build-secure-enterprise-ml-platform/personas-for-an-ml-platform.html)
1. [Red Hat - Your Guide to the Red Hat Data Science Model Lifecycle](https://cloud.redhat.com/blog/your-guide-to-the-red-hat-data-science-model-lifecycle)
1. [Domino Data Labs - 7 Key Roles and Responsibilities in Enterprise MLOps](https://www.dominodatalab.com/blog/7-roles-in-mlops)
1. [AWS - MLOE-04: Establish ML roles and responsibilities](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mloe-04.html)
