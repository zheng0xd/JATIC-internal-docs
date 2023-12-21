# Persona: Platform Engineer

# Name: Pax

## Quote
<!--Describe the role from the persona perspective.  What does this persona want to accomplish in their usual work?-->
> I like to work with users to make sure their software and pipelines are deployed easily. I'm always keeping an eye on security and efficiency. I always look for ways to automate and simplify processes. Helping others deploy their projects can be challenging but fun.

## Demographic information
* **Experience**: 8 years in IT
* **Education**: BS in Computer Science
* **Job Title**: Platform Engineer

## Goals and motivations
<!--What is the mission that they are working on?-->
<!--What is the AI modality and use case(s) that they are working on?-->
<!--What are the models and/or datasets that they are working with?-->
<!--What is their role on this project? What task are they trying to achieve?-->
The platform engineer is focused on infrastructure and access. 

Regarding the platform itself, the platform engineer is in charge of maintaining the deploying the platform. This includes maintaining the GitOps deployment pipeline and the underlying infrastructure, ensuring access to the appropriate cloud resources for deployment, and ensuring continuous availability. The platform engineer also oversees security and the creation of new users and granting/maintaining their access to different aspects of the platform and infrastructure. 

## Challenges and obstacles
One of the biggest challenges of the Platform Engineer is knowing and understanding the needs of the end users. It is a challenge to ensure that resources are made available when it is not clear what resources will be required. Another big challenge is ensuring uninterrupted availability of the platform. The GitOps approach is a great help here, but over time there will always be infrastructure maintenance challenges.

## Behaviors and preferences
<!--How do they interact with technology? -->
<!--What are their typical behaviors, preferences, and struggles?-->
Pax comfortable with a high degree of autonomy. They appreciate tools and technologies that allow for efficiency, automation, and scalability.

They are comfortable working in a wide variety of environments. They understand bash scripts, python, terraform, and helm to name a few. They typically work in Linux systems but are flexible. 

## Background and experience
<!--What's their experience with AI, AI T&E, or other relevant domains? What other skills do they bring to the table?-->
Pax has a strong background in IT and systems engineering. They have deployed various platforms on cloud and local infrastructure. They have a strong Dev Ops background and are comfortabe with scalable compute such as kubernetes. They are also proficient in several programming languages, and have a deep knowledge of cloud technologies.

## User story: 
<!--What is an example of a scenario where the persona would use the tools? What are they trying to accomplish?-->
Pax has been tasked with deploying a user-facing Jupyterhub-based platform on which AI engineers will develop and launch models. They need to ensure that the infrastructure is set up correctly, that models can be deployed seamlessly, and that the deployment pipeline is secure and efficient. They use their knowledge of bash scripts, python, terraform, and helm to set up the environment, configure the deployment pipeline, and troubleshoot any issues that arise during the deployment process. Pax is also responsible for adding/removing userss and setting appropriate permission levels for users. 

## Working Environment

<!--What environment are they performing their mission in?-->
<!--What OS? System tybe? Classification level?-->
<!--What other tools are they using? How must other tools integrate with them?-->

Pax is a remote employee that spends much of their day logged into remote machines via their Linux laptop. They work primarily AWS GovCloud resources but are also familiar with other cloud services.

## Relevant JATIC Tools
<!--Which JATIC tools or functionalities may be of interest to them?-->
Pax doesn't use JATIC tools directly but rather ensures that end users have the infrastructure required. 

## Workflow
<!--Given this persona, construct a workflow, mapping out its various steps-->
<!--Feel free to refine and copy over the workflow diagram from MURAL as an image-->
The Platform Engineer workflow for deploying a Nebari platform:
* Set up credentials and access to the platform cloud resources (or local as needed)
* Set up the initial git repo following the guided init CLI
* [Optional] modify `nebari-config.yml` as needed to add any additional resources, etc. 
* Enable GitOps based on `nebari-config.yml` to ensure that auto redeploy and reproducibility are in place. 

## References

<!--If applicable, list any references for this persona, including generic references and specific DoD user groups who may be represented within this persona-->
