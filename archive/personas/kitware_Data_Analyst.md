# Persona: Data Analyst

## Role and Background

<!--What's their name and role?-->
<!--What's their experience with AI, AI T&E, or other relevant domains? What other skills do they bring to the table?-->

- Name: Maxwell
- Role: DoD Contractor
- Education: B.S. in Biomedical Engineering
- Experience: Works primarily on medical imaging problems

## Mission and Goals

<!--What is the mission that they are working on?-->
<!--What is the AI modality and use case(s) that they are working on?-->
<!--What are the models and/or datasets that they are working with?>
<!--What is their role on this project? What task are they trying to achieve?-->

Maxwell is working on a digital pathology problem, where he is helping create a "super" dataset for training models on whole slide images. His hypothesis is that including multiple datasets and standardizing their formats and labels will improve model performance by increasing the size and diversity of training samples. He needs to survey existing datasets, assess their quality and applicability to the given task, and create a report on the statistics of each dataset. He may also assist in creating functions for loading in the final dataset (e.g. a Pytorch DataLoader utility).

## Preferences and Challenges

<!--How do they interact with technology? -->
<!--What are their typical behaviors, preferences, and struggles?-->

Maxwell needs methods for efficiently handling large volumes of data and standardizing their formats. This might include a central data store or workflows for efficiently pulling down data and visualizing dataset examples. From a data quality perspective, he also needs to ensure that there are no duplicates in the data (and across datasets), which could result in data contamination and bias model evaluation results. Finally, he may need to assess different dataset licenses (sometimes in consultation with his compliance team) to ensure that they can be used on his project. 

## Working Environment

<!--What environment are they performing their mission in?-->
<!--What OS? System tybe? Classification level?-->
<!--What other tools are they using? How must other tools integrate with them?-->

Maxwell has a prototypical data scientist background, so he works primarily in Python using Jupyter notebooks for development, which could come from other providers (e.g. Databricks or Amazon Sagemaker). He is familiar with standard visualization libraries (e.g. matplotlib and seaborn), as well as tools for querying and analyzing data (e.g. SQL and pandas). He is cognizant of potential protected health information (PHI) constraints, although he currently plans to only work with de-identified data.

## Relevant JATIC Tools

<!--Which JATIC tools or functionalities may be of interest to them?-->

* Dataset Cards
* Label Error Analysis
* Sufficiency Analysis
* Bias and Explainability
* Dataset Utilities (e.g. splitting, merging, etc.)
* Visualization

## Workflow

<!--Given this persona, construct a workflow, mapping out its various steps-->
<!--Feel free to refine and copy over the workflow diagram from MURAL as an image-->

[Link to workflow in Mural](https://app.mural.co/t/ecis6578/m/ecis6578/1684176213416/a46fdab86d52a0891ebb89a51c8d7f1273fbde0c?sender=213eee12-6851-4833-a6d3-746cbb3f1b1a)

## References

<!--If applicable, list any references for this persona, including generic references and specific DoD user groups who may be represented within this persona-->
