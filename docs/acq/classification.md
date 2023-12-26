# Classification Strategy

This page details the classification level of products within the program, as well as consequent program limitations and risk controls.

## Classification level

The program manger has determined that the software developed under the JATIC program will be unclassified, in order to most effectively meet the above capability need. 

!!! note

    The program designating products as unclassified does not preclude their use within classified networks, or the creation of extension modules which are classified at higher levels.

### Capability need

The design of these products to only include unclassified information is critical for fulfilling the above capability need. 

`LOE 2.1.1` within the _Responsible AI Strategy and Implementation Pathway_ mandates the AI T&E Toolkit to be made widely available to DoD users, and `LOE 2.1.3` mandates a central repository for these tools. Classifying these products at higher levels would greatly restrict availability to the DoD enterprise.

### Constraints on software

The following constraints will be placed upon all software developed within the program:

1. Shall not include information about any specific AI systems
1. Shall not include any of the data that is required to test AI systems
1. Shall not provide T&E Master Plans, Test Plans, metrics thresholds, or metric objectives of the capabilities of an AI program, mission, or line of effort
1. Shall not describe the tactics, techniques, or procedures used to evaluate the capabilities of an AI program, mission, or line of effort
1. Shall not include details on the vulnerabilities, performance, accuracy, efficiency, reliability, other metrics, or reports of capabilities of an AI program, mission, or line of effort
1. Shall not include techniques to test any AI model modalities, sensors, or systems that are DoD-unique (i.e., products shall be applicable generically to research or commercial AI models)

### Consistency with guidance

This classification is consistent with the following elements of DoD and USG guidance:

1. _Joint AI Center (JAIC) Security Classification Guide (SCG)_, Section 3, Topics 44, 45, 50, and 113.
1. _DoD CIO Memo on Software Development and Open Source Software_, Main memo & Attachment 2
1. _Executive Order 13526_, Section 1.4
1. _Mitigating the Risk of Software Vulnerabilities by Adopting a Secure Software Development Framework (SSDF)_, NIST

## Risk management

The program will employ the following processes and design practices in order to ensure that software developed within is appropriate for the level of classification.

### Review process

Within the initial planning process each development team will confirm and vet their lines of development, functionalities, and capabilities with the program management team. Periodic manual reviews (e.g., at development “sprint” planning meetings) will keep the work within bounds.

Software quality will be monitored and enhanced by applying software engineering best practices.

- A “linter” will be applied to flag common programming concerns and enforce consistent source code style. 
- Continuous integration (CI) and continuous delivery (CD) workflows will be implemented to automatically build and test the software on a regular basis. 
- The current state of the repository will be indicated with “badges” for properties such as build status, unit test results, documentation, and code coverage. 

In addition to automated quality control measures, code will be reviewed for quality and regularly tested by independent government testers who will control the quality and security of deliverables.

### Modular approach

In accordance with the DoD CIO Memo on Software Development, the risk of code developed for DoD systems potentially benefitting adversaries will be managed through adopting a Modular Open-Systems Approach (MOSA) within all products.

The program will provide a software foundation upon which other organizations may build modules that are more specially tailored to their mission use cases. This approach provides the ability for a wide distribution of foundational software, while protecting critical, innovative components as separate modules.

### System or program-specific information

JATIC products will not reveal, contain, describe, or include information on specific AI models, AI-enabled systems, AI programs, missions, or lines of effort. They will include neither data, nor models, nor metrics, nor vulnerabilities, nor results, nor specific tactics, techniques, or procedures used, nor thresholds or objectives to achieve.

In addition, JATIC products will only include techniques which are applicable to AI model frameworks and modalities that are commonplace within research and industry. In particular, the program will develop tools for evaluation of CV Object Detection and Classification, two of the most common tasks found within AI research. It will not develop tools to test DoD-unique technology categories, such as DoD-unique sensors or DoD-unique AI-enabled systems. Testing software of this sort must be extremely tailored to the system, and may be appropriate for classification relative to the system that they are tailored to.

### Datasets, models, and third-party software

Development and testing will be driven by open-source datasets (such as CIFAR-10 and ImageNet, which are common benchmarks used in computer vision research) and open-source AI models. No new data sources will be distributed within the program. Any examples, data samples, or pre-trained models that are used as examples within the program's documentation will be derived from open datasets or publicly available sources.

The program will not redistribute any embedded third-party software. However, in their descriptions, products will list all core dependencies required to be present in the environment for our software to be able to run.
