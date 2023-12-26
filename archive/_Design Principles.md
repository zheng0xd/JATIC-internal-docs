
# Design Principles

## Introduction

This document traces the development of a number of design principles of JATIC software.

## Review of previous capabilities

### Limitations in previous capabilities

While AI T&E capabilities developed by previous DoD AI Programs have been functional, none of them are sufficient as an enterprise-wide solution. Below, we provide our observations as to what shortcomings these AI T&E capabilities had. To be fair, these capabilities were not designed to be enterprise-wide solutions, but instead were developed to solve the T&E problems which were particular to their AI program. With that caveat in mind, here are several key factors which have limited previous capabilities from becoming widely used and distributed across the Department:

1. Difficulties in deployment
   1. Capabilities were difficult to deploy to environments across the DoD. Even applications which were delivered as containers were extremely difficult to deploy and orchestrate in new environments, often requiring extensive effort from cloud engineers and the development team.
   2. Common errors included configurations in helm charts or docker-compose files, permissions issues, and incompatible changes between software versions.
2. Difficulties in standardization
   1. Capabilities often did not support common AI/ML model formats (e.g., TensorFlow/Keras, PyTorch, MXNET) or data ground truth formats (e.g., csv, json, or serialized formats) that are used within industry and academia. This was often because they were developed with a specific AI application in mind. This demanded model and data wrangling into different standards to use different capabilities.
   2. This lack of support for the common standards used in industry and academia also made it difficult for the capabilities to evolve with developments in the state-of-the-art, such as new algorithms and techniques, which often built on existing formats.
3. Difficulties in integration with platforms
   1. Capabilities did integrate easily with the main platforms and tools through which AI programs used to develop and manage their AI. For example, the CDAO ADVANA platform uses Databricks and MLFlow for its AI, and Army AI Integration Center uses the COEUS platform. For example, capabilities often required users to leave the platform and use another application entirely.
   2. Often, applications had a completely different UI, different processes for setting up data and models, etc. For example, some tools may interface through a REST API, with all experiment variables configured through a .json file. Other may be configured through a GUI, with experiment variables configured through dropdowns.
4. Integration with supporting T&E functionality
   1. All T&E capabilities required a foundation of key functions in order to be effective. These functions included
      1. an automation pipeline to kick off T&E experiments
      2. a dashboard to visualize results
      3. an experiment tracking system to associate metrics with model runs
      4. a object storage database
      5. a model inference server
   2. T&E capabilities often provided their own bespoke solutions to the above, including their own visualization dashboards, automation pipelines, etc. But, ML pipelines often had a great deal of these capabilities built in.
   3. Thus, using multiple capabilities within an ML pipeline often meant spinning up multiple object storage databases, dashboards, automation pipelines etc. which was confusing and inefficient.
5. Lack of maturity, polish, cybersecurity, scalability, etc.
   1. While capabilities could often be made to work, they almost never had the level of maturity of fully developed and productized software.
   2. This showed in a number of areas, including the quality of the UI, the detail of the documentation, the level of cyber-hardening, and the performance of the capabilities when used at scale.
6. Lack of discovery of the capability
   1. A program may have had great functionality but it was not easy or possible for other teams to discover it

The above limitations did not operate in isolation, but rather, intersected with and compounded on themselves. A Program Office developing AI that wanted to use two such T&E capabilities, perhaps one for automated metrics calculation and another for adversarial robustness testing, would have to engineer the deployment of both into their environment, integrate both with their current tools and platforms, create model and data format converters to work with both capabilities (often expecting different formats), and use separate programs to interact with each (perhaps a separate GUI for one, and a command-line interface for another).

Because of the challenges with existing capabilities, many programs developing AI created their own bespoke capabilities to address their T&E gaps, limited themselves to calculating basic T&E metrics (e.g., precision, accuracy, recall, F1 score, etc.), or relied on reported metrics from the model vendors. None of these solutions were satisfactory - either the AI was not sufficiently tested, or funding was suboptimally spent on the development of another tool with limited applicability and similar functionality to existing tools.

## Maximizing the effectiveness of T&E

The examination of previous capabilities indicates that the deep integration of T&E capabilities with other technologies within the AI/ML lifecycle creates powerful synergistic effects that increase the effectiveness of the whole. For example, it is extremely valuable for the T&E metrics computed to feed into a centralized model registry, to be logged in the experiment tracker, to be able to be used as a target for the hyperparameter optimizer, and to be able to be visualized within a dashboard.

This effect also holds for between different T&E capabilities themselves: they work best when they are able to be used in combination with each other. For example, if there are three T&E capabilities for 1) automated metrics calculation, 2) adversarial attacks, and 3) explainability and saliency maps, it may be extremely interesting for a user to understand an adversarial attack on an image by understanding the change in the corresponding saliency map after the attack is produced. It may also be extremely helpful to automate the computation of adversarial attacks and explainability techniques into the metrics calculation pipeline. T&E capabilities which are unable to integrate with each other and other technologies disguise the true potential of T&E both in itself and as an AI-enabler.

Palantir's Data Management Platform demonstrates a successful approach to integration: to own the entire vertical, end-to-end pipeline. This approach is not one that is practical to adopt, since it calls for the development not of a testing capability, but rather a comprehensive platform for data and ML which includes testing functionality as one component.

It cannot be the case that JATIC, which is designed to be an enterprise-wide capability for CV model T&E, also dictates every other component of the data and AI process. First of all, JATIC is not funded to do this. Second, programs offices, agencies, and organizations throughout the Department will leverage many different platforms based on their mission need. JATIC should be able to deliver T&E capability to support a wide range of these organizations, no matter what larger platform they choose to use for their data storage, labeling, model training, dashboarding, model monitoring, etc.

From all of the above, we summarize the following principles:

1. JATIC cannot become an end-to-end platform that includes all functionality required for the AI/ML lifecycle; JATIC's functionalities should be limited to T&E itself.
1. In order to deliver value across the DoD enterprise, JATIC must be able to deploy and operate in a wide variety of environments across the Department.
1. In order to maximize the effectiveness of T&E for a given program developing AI, JATIC must be able to integrate into other AI/ML platforms, frameworks, and technologies used by that program.

## ML platforms

For many industry organizations developing and deploying AI in production, the foundational technology stack is the end-to-end ML platform. For creating AI models in production, the actual model weights are only one small piece of the puzzle. Automation, tracking, scalability, deployment, and monitoring all emerge as difficult problems when AI must work in a production environment. ML platforms often provide solutions for the range operations necessary for the AI/ML lifecycle, including:

1. Data: Data cleansing, data ingestion, exploratory data analysis, data transformation, data validation, feature engineering, data splitting, data versioning
1. Models: model training, training optimization, model validation, training at scale, model registration, model storage
1. Deployment: model deployment, model serving, model monitoring, model logging, model retraining
1. Support: Automation, workflow orchestration, dashboarding, visualization, collaboration

There are numerous platforms available for this purpose. Many companies have developed their own in order to train and deploy their AI models at scale, including Uber's Michelangelo, Facebook's Learner, and Airbnb's Bighead. Major solutions offered as a service include AWS Sagemaker, Azure Machine Learning, Google Cloud AI Platform, and Databricks. A great article for more information is [a tour of end-to-end ML platforms](https://databaseline.tech/a-tour-of-end-to-end-ml-platforms/).

### DoD's ML platforms

Our observation is that program offices, agencies, and organizations developing AI across the DoD have recently recognized the need for ML platforms. Many organizations are developing their own, uncoordinated with others. The focus among these platforms varies based on the mission need: some are focused on data science, some on model development, some on post-deployment monitoring and model retraining. Some examples across the DoD include:

1. DoD CDAO - ADVANA
   1. "DoD's big data platform for advanced analytics"
   2. "Advana is a centralized data and analytics platform that provides DoD users with common business data, decision support analytics, and data tools"
   3. ADVANA is also gaining MLOps capabilities to support machine learning development and testing workflows.
2. Joint AI Center - Joint Common Foundation
   1. "The DoD’s Cloud-Based AI Development and Experimentation Platform"
   2. "The Joint Common Foundation (JCF) is a secure cloud-based AI development and experimentation environment that delivers critical tools and capabilities to support the DoD’s pursuit of an AI-ready force."
3. NIWC / DIU - Project AMMO
   1. An MLOps platform to support rapid retraining, deployment, and monitoring of AI models on unmanned underwater vehicles.
4. Air Force - Platform One
   1. "Platform One (P1) is a modern cloud-era platform that provides valuable tooling, hosts CI/CD DevSecOps pipelines, and offers a secure Kubernetes platform for hosting microservices."
   2. Initially focused on DevSecOps, but now getting augmented with MLOps pipelines to support AI/ML development.
5. AFRL - RedForce
   1. A set of cloud services and capabilities to enable rapid delivery of AI.
6. Army Futures Command - Project COEUS
   1. "'Open Community Data Science Platform' to support autonomy and artificial intelligence requirements"
   2. "The aim of COEUS is to enable the development and deployment of AI capabilities faster than previously possible. COEUS provides a way to collect usable data—often in real time as it comes in from the field—curate it, use it to effectively train AI models, and deploy them quickly as threats emerge."
7. Army PM IS&A - ArcaneFire, TITAN
   1. "An AI/ML pipeline ... for model training, management, and deployment of AI/ML models."
   2. Uses Databricks, MLFlow, Delta Lake, and rsync for its ML platform.
8. Army PEO IEWS - Project Linchpin
   1. "Next-Generation IEW&S sensors will be ineffective without a pipeline to train and deliver AI/ML. AI/ML capabilities must be continuously integrated and continuously delivered (CI/CD). Data sets should be centrally held; data ontology, categories, and labels should be standardized."
   2. "Project Linchpin delivers an AI/MLOps “Pipeline as a Product” (PaaP) for IEW&S sensors."
9. Army PEO C3T - AI Pathfinder
   1. "PEO C3T is executing an AI Pathfinder that aims to reduce the time to develop and deploy AI-based capabilities from years down to months."
   2. "Standardize AI-enabling IT infrastructure and DevOps/DevSecOps processes to enable smoother transition of AI capabilities from labs to warfighters."

Most of these platforms use an amalgamation of open-source and commercial-off-the-shelf solutions to create their pipeline. Other platforms, like ADVANA, adopt an end-to-end solution such as Databricks as the foundation, and fill in the gaps with other capabilities.

**We hypothesize that as more program offices begin to develop AI, there will be more such platforms that emerge across the Department. Furthermore, unless the data storage and compute infrastructure become more centralized across the Department, these emerging platforms will be highly varied in their AI technology stack.**

Thus we encounter another principle:

In order to deliver value across the DoD enterprise, JATIC must be able to integrate into a wide variety of AI/ML platforms and technologies, including those that are currently used across the Department and *those that will be adopted in the future.*

### ML Platforms and T&E capability integration

The central functionalities which are provided by ML platforms which are critical for T&E include automation, visualization, tracking, and orchestration at scale. This is worth noting.

T&E capabilities, including JATIC, must

1. be able to be automated within a model delivery pipeline
2. have results that can be visualized and interactively explored within a visualization dashboard
3. have results that can be tracked to compare models with each other and over time
4. be able to scale efficiently

These functions are necessary for a successful T&E pipeline, but T&E capabilities should not necessarily seek to create their own competing implementations. Many ML platforms already provide such functionalities, and one would need to invest a great deal of money to create a competing platform that could convince another to move away from Databricks, Sagemaker, or the bespoke AI/ML solution which has been heavily invested in. Besides comprehensive ML platforms, other technologies also provide general functions for the above, such as Apache Airflow for workflow automation.

Instead of recreating functionalities for automation, visualization, and tracking, JATIC should be designed to modularly interoperate with existing ML platforms and technologies that offer these critical supporting functions.

Next emerge the questions of implementation: How is it that JATIC should design its capabilities such that they can integrate into a wide variety of the above ML platforms? Is such a design even feasible? What are the drawbacks and limitations to such a general design?

We propose python libraries as a software form factor that allows wide integration with ML platforms and technologies. The following observations support provide support.

1. A common interface throughout nearly all of the ML platforms is python code through various types of interactive python notebooks.
1. Orchestration engines, which create the pipelines between modular components of an ML platform, widely support python code components.
1. ML models and ML technologies are often interacted with through python code.

In addition to software form factor, JATIC functions should be designed with intelligent interfaces to allow wide compatibility with the above technologies.

JATIC software will be designed as python libraries with interfaces that are widely compatible with common ML platforms, model frameworks, data formats, and enabling technologies.

## Two critical dimensions of users

We identify two critical dimensions of JATIC users along which create greatly different requirements and methods of value delivery.

1. Platform-locked vs Platform-free - This dimension refers to the level of commitment that a user has to a certain ML platform. A platform-locked user may be part of an organization that has already committed to using certain platforms for their data and ML. While we note above that many DoD organizations are adopting ML platforms, a large amount of the AI being developed and tested within the Department is still done ad-hoc, without a platform-level solution. These users may not be committed to any fixed technologies.
1. Tech-savvy vs not tech-savvy - This dimension refers to the level of technical competence of a user. A tech-savvy user is one who is at least familiar with python, jupyter notebooks, and reading technical documentation.

We believe that these two distinctions are some of the most important among potential users of not only JATIC software, but of AI/ML technology across the DoD. When wanting to use any given AI/ML technology out there (for example, take any technology on <https://landscape.lfai.foundation/>) the two preeminent questions are:

1. Does the technology exist on the cloud platform or environment on which work is done? This is especially important in classified environments.
1. Does the user have the technical experience and know-how to use the technology?

Below, we present examples of a user persona within each quadrant of these two dimensions and some things they may care about within a T&E capability, ranked from most important to least important.

- Savvy, Platform-locked
  - Ex: Databricks ML developer
  - Wants tools that usable seamlessly with their ML platform
  - Wants tools that give deep new model insights, including complex and technical T&E functions
  - Wants tools that can integrate flexibly into a number of ML technologies
  - Wants tools that greatly simplify previously tedious processes
- Non-savvy, Platform-locked
  - Ex: Non-technical test engineer whose T&E data lives on ADVANA must use ADVANA's Databricks pipeline
  - Wants tools that are simple to setup and use
  - Wants tools that usable seamlessly with their ML platform
  - Wants tools that enable easy, automated, and documented T&E
- Savvy, Platform-free
  - Ex: Test engineer who is comfortable with python but has not used an enterprise ML platform
  - Wants tools that give deep new model insights, including complex and technical T&E functions
  - Wants tools that can integrate flexibly into a number of ML technologies
  - Wants tools that greatly simplify previously tedious processes
- Non-savvy, Platform-free
  - Ex: Non-technical test engineer who's organization does not have an enterprise ML platform. T&E data lives on S3 bucket and compute performed on an on-prem cloud
  - Wants tools that are simple to setup and use
  - Wants tools that enable easy, automated, and documented T&E

We hypothesize that the platform-locked groups make up most of our large customers, while many smaller organizations are platform-free. Successful delivery and support for these two groups will look different, since an integration with a large customer's platform (e.g., ADVANA) may expose our capability to many users at once and may require large agreements, while smaller groups without platforms will be more ad-hoc.

## Limitation: Non-savvy users & technical complexity

The most important consideration for non-savvy users is ease of setup and use. This is fundamentally in tension with the design of not only JATIC (as python libraries), but also with nearly all AI/ML technologies, which use code as the primary interface.

While T&E itself is not an activity that fundamentally requires code (one can perform T&E through the selection of models, datasets, and parameters within dropdown menu GUIs), a code interface greatly enhances the flexibility, power, and integrations that T&E capabilities can have. ML model development is similar - parameter configuration and model training could be accomplished in a GUI (select model architecture, weights, training step, etc. and train), but the python form factor adds much more flexibility. Lack of technical familiarity, at least with python, is a hurdle that the DoD will need surmount in order to increase its effectiveness in AI development, testing, and deployment.

## GUIs

The natural response to support the non-savvy userbase is to create a comprehensive GUI-based application from which T&E capabilities can be used. We think this is correct, but it is extremely important how the design of this GUI-based application is undertaken.

### Difficulties in developing GUI-based applications

It is easy to develop a GUI-based application which sacrifices all of the other principles and requirements noted in this document, such as integration with other technologies, ease of deployment, and automation. Additionally, developing a successful GUI is a deceptively difficult endeavor. There is little that is more off-putting than a badly designed GUI. The use of several tools, each with their own independent GUI design, may be incongruent and jarring. A GUI is much more difficult to keep polished and updated than code. A GUI which spans capability of multiple developers requires much more integration effort than code integration. A GUI should be developed in close coordination with the end-users, to ensure that it aligns with their workflow. Finally, GUI development is generally expensive.

### Advantages of interactive interfaces for T&E

On the other hand, many T&E tools greatly increase in richness when paired with an interactive interface. For instance XAI saliency maps are much more useful as an interactive display, where the user can tweak parameters and see the changes to the heat map on an image, rather than a series of static images.

A solution which provides an interactive interface while avoiding many of the difficulties above involves the usage of a library that can build GUIs in pure python and embed within python notebooks. This approach has the following advantages:

1. allows the GUI to be usable within many environments such as Databricks directly within experimentation notebooks, without an additional web server
2. provides a standardized library that all vendors can use, and therefore, a standardized GUI experience
3. makes GUI creation and iteration extremely easy, even for those without any training in front-end development
4. expands T&E tools by providing interactivity and immediate feedback

We propose the use of Gradio (<https://www.gradio.app/>). While many applications can be used to develop web-based UIs (see <https://towardsdatascience.com/gradio-vs-streamlit-vs-dash-vs-flask-d3defb1209a2>), Gradio's ease of UI development and ability to embed in Jupyter notebook outputs makes it most appropriate for our usage.

Each T&E capability will develop a series of widget in Gradio that allow for the usage of the capability's underlying functions in an interactive way. For example, an XAI saliency capability would develop a widget that would allow the user to provide choose a model, saliency technique, image, and parameters as inputs, and display the saliency map as an output. The inputs could be tweaked interactively, for instance, numerical inputs on a slider bar.

We propose that a more extensive GUI-based application is developed later, after the foundational code capabilities have been developed and we have a concrete group of users.

## Limitation: Platform-free users & lack of functionality

We noted above that automation, tracking, and visualization are critical components for any AI T&E pipeline. We also noted that T&E capabilities should not attempt to create this functionality, since it exists within many ML platforms or other ML technologies, and the functionality often spans beyond that of T&E. However, since we propose that JATIC does not provide this functionality, the JATIC does not reach full potential for platform-free users until this functionality is obtained. This makes JATIC a difficult product to adopt for platform-free users, since the tools seem disparate (rather than a single T&E solution) and lacking in core functionality such as experiment tracking. Giving users the ability to plug in their own solutions increases interoperability, but also increases complexity, especially for users who are unfamiliar with the space of solutions.  

## JATIC preferred platform

For this group, it may also be the case that a single, unified T&E platform may greatly simplify and standardize ML testing and development. To these users, JATIC can be delivered as a bundle, with an industry standard automation, tracking, and artifact storage solution, as the **JATIC preferred platform**. This is the position the position that was previously fulfilled by standalone, GUI based T&E tools, which we called "Tier 2" tools (as opposed to "Tier 1" tools, which were python libraries).

This unified T&E platform also works well in conjunction with the T&E GUI as a single solution that can be easily adopted by non-savvy, platform-free users for comprehensive T&E.

## Limitation: Design within constraints of ML platforms

It is obvious that one has more control in capability design when one designs all components of the capability, rather than requiring integrating into existing capabilities. In outsourcing many critical T&E functionalities to other platforms and technologies, JATIC takes on a large number of design constraints. A central challenge of JATIC will be to create powerful T&E capabilities within this smaller design space.

An example: ML platforms like MLFlow and Sagemaker provide dashboards for visualization of model metrics. Are these sufficiently flexible to allow visualization of explainable AI saliency maps? To visualize interactive performance curves? To explore examples of model misclassifications? If not, what is a solution that does not compromise ease of integration and deployment?
