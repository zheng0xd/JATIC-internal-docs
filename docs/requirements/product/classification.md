# Classification Policy

This page details the classification policy of products within the program, as well as consequent program limitations and risk controls

## Classification level

In order to most effectively meet capability needs, software products and other artifacts developed under the program will be unclassified.

!!! note

    The program designating products as unclassified does not preclude their use within classified networks, or the creation of extension modules which are classified at higher levels.

This is critical for fulfilling `LOE 2.1.1` within the _Responsible AI Strategy and Implementation Pathway_, which mandates that AI T&E products are made widely available to DoD users. Classifying these products at higher levels would greatly restrict availability to the DoD enterprise.

### Constraints and limitations

Software and artifacts developed within the program:

1. Shall not include or describe information on any specific DoD AI models, AI-enabled systems, programs, or missions
1. Shall not include or describe the data, models, metadata, or parameters of any specific DoD AI models, AI-enabled systems, programs, or missions
1. Shall not include or describe details on the vulnerabilities, performance, accuracy, efficiency, reliability, other metrics, or reports of any specific DoD AI models, AI-enabled systems, programs, or missions
1. Shall not include or describe the tactics, techniques, or procedures used to evaluate the capabilities of any specific DoD AI models, AI-enabled systems, programs, or missions
1. Shall not provide T&E Master Plans, Test Plans, metrics, metrics thresholds, or metric objectives of the capabilities of an AI program, mission, or line of effort
1. Shall not include techniques to test any DoD-unique AI model modalities, sensors, or systems

### Consistency with guidance

This classification determination is consistent with the following elements of DoD and USG guidance:

1. _Joint AI Center (JAIC) Security Classification Guide (SCG)_, Section 3, Topics 44, 45, 50, and 113.
1. _DoD CIO Memo on Software Development and Open Source Software_, Main memo & Attachment 2
1. _Executive Order 13526_, Section 1.4
1. _Mitigating the Risk of Software Vulnerabilities by Adopting a Secure Software Development Framework (SSDF)_, NIST

## Risk management

The program will employ the following processes and design practices in order to ensure that software developed within is appropriate for the level of classification.

### Review process

The program will implement a review process as detailed in the [Software Development Plan TBD].

### Datasets, models, and third-party software

Development and testing will be driven by open-source datasets and models. 

No new data sources will be distributed within the program. Any examples, data samples, or pre-trained models that are used as examples within the program's documentation will be derived from open datasets or publicly available sources.

The program will not redistribute any embedded third-party software. However, in their descriptions, products will list all core dependencies required to be present in the environment for our software to be able to run.
