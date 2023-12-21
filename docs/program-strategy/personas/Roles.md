# Roles

The software developed within our program will support a number of different types of users within the AI Lifecycle. We call types of users, "roles".

We identify the following as different roles we may support. Other roles may be identified. We will support roles by creating personas representing the role, creating workflows for the personas, and creating tools to support the persona and workflow. Roles should be defined in this document and then used in personas. 

1. AI T&E Engineer
2. ML Developer
3. Data Analyst
4. AI Red Teamer

## 1. AI T&E Engineer

- Measure performance of models within various settings and contexts
- Compare performance of models
- Verification of requirements satisfaction and validation of evaluation results
- Quantitative evaluation of risks
- Explore potential unknown risks
- Develop summary report of findings
- Not a developer of the system

## 2. ML Developer

- Exploratory data and model analysis
- Statistical analysis
- Model experimentation
- Feature engineering
- Model training and continuous fine-tuning
- Uses MLOps, end-to-end model pipelines

See Data Scientist and ML Engineer in [1], and Data Scientist in [2] and [3] for references and a general job description. We're calling this ML Developer, since data scientist is easily confused with the following role. 

## 3. Data Analyst

- Data visualization and analysis
- Statistical analysis of dataset properties
- Data set selection, curation, and validation
- Data preparation and cleaning

See Data Analyst in [3] and [4] for references and a general job description. Note that there is the potential for confusion with IC-background people, since analyst often means something different in that context.

## 4. AI Red Teamer

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