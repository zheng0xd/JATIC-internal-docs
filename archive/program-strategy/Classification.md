# Classification

## JATIC MVP Classification

The JATIC Program will create software to enable the T&E of AI models, primarily as python libraries.

The Program Manger has determined that the software developed under the JATIC Program Minimum Viable Product (MVP) will be Unclassified, in order to most effectively meet the above capability need. The following constraints will be placed upon all software developed within the JATIC MVP:

1. Shall not include information about any specific AI systems
1. Shall not include any of the data that is required to test AI systems
1. Shall not provide T&E Master Plans, Test Plans, metrics thresholds, or metric objectives of the capabilities of an AI program, mission, or line of effort
1. Shall not describe the tactics, techniques, or procedures used to evaluate the capabilities of an AI program, mission, or line of effort
1. Shall not include details on the vulnerabilities, performance, accuracy, efficiency, reliability, other metrics, or reports of capabilities of an AI program, mission, or line of effort
1. Shall not include techniques to test any AI model modalities, sensors, or systems that are DoD-unique (i.e., JATIC tools are applicable generically to research or commercial AI models)

This classification is consistent with the following elements of DoD guidance:

1. Joint AI Center (JAIC) Security Classification Guide (SCG), Section 3, Topics 44, 45, 50, and 113.
1. DoD CIO Memo on Software Development and Open Source Software, Main memo & Attachment 2
1. Executive Order 13526, Section 1.4
1. NIST White Paper, "Mitigating the Risk of Software Vulnerabilities by Adopting a Secure Software Development Framework (SSDF)"

In addition, the design of MVP JATIC software to only include unclassified information is critical for fulfilling the above capability need. LOE 2.1.1 within the RAI S&I Pathway mandates the AI T&E Toolkit to be made widely available to DoD users, and 2.1.3 mandates a central repository for these tools. Currently, the DoD Centralized Artifact Repository and Source Code Repository are at IL2. There are no mechanisms to make CUI source code widely available to DoD users. Thus, MVP JATIC software will be developed in such a way that all materials within the program are Unclassified.

## Risk Management

The JATIC program will employ the following processes and design practices in order to ensure that software developed within the MVP is appropriate for the level of classification.

### Review Process

Within the initial planning process each development team will confirm and vet their lines of development, functionalities, and capabilities with the JATIC program management team. Periodic manual reviews (e.g., at development “sprint” planning meetings) will keep the work within bounds.

Software quality will be monitored and enhanced by applying software engineering best practices. A “linter” will be applied to flag common programming concerns and enforce consistent source code style. Continuous integration (CI) and continuous delivery (CD) workflows will be implemented to automatically build and test the software on a regular basis. The current state of the repository will be indicated with “badges” for properties such as build status, unit test results, documentation, and code coverage. In addition to automated quality control measures, code will be reviewed for quality and regularly tested by independent government testers who will control the quality and security of deliverables.

### Modular Open Systems Approach

In accordance with the DoD CIO Memo on Software Development, the risk of code developed for DoD systems potentially benefitting adversaries will be managed through adopting a Modular, Open-Systems Approach (MOSA), within all of JATIC software packages.

Note that an Unclassified MVP of JATIC clearly does not preclude the use of JATIC for classified or sensitive work, or the creation of additional modules at higher levels of classification. The JATIC MVP will provide a software foundation upon which later years of the program may build modules that are more specially tailored to mission use cases. This approach provides the ability for a wide distribution of JATIC foundational software, while protecting critical, innovative components as separate modules.

### System or Program Specific Information

JATIC will not reveal, contain, describe, or include information on specific AI models, AI-enabled systems, AI programs, missions, or lines of effort. It will include neither data, nor models, nor metrics, nor vulnerabilities, nor results, nor specific tactics, techniques, or procedures used, nor thresholds or objectives to achieve.

In addition, the JATIC MVP will only include techniques which are applicable to AI model frameworks and modalities that are commonplace within research and industry. In particular, the JATIC MVP will include tools for evaluation of CV Object Detection and Classification, two of the most common tasks found within AI research. JATIC will not include tools to test DoD-unique technology categories, such as DoD-unique sensors or DoD-unique AI-enabled systems. Testing software of this sort must be extremely tailored to the system, and may be appropriate for classification relative to the system that they are tailored to.

### Datasets, Models, and Third-Party Software

Development and testing will be driven by open-source datasets (such as CIFAR-10 and ImageNet, which are common benchmarks used in computer vision research) and open-source AI models. No new data sources will be distributed within JATIC. Any examples, data samples, or pre-trained models that are used as examples within JATIC documentation will be derived from open datasets or publicly available sources.

We do not plan to redistribute any embedded third-party software. However, in software description, we will list all core dependencies required to be present in the environment for our software to be able to run.
