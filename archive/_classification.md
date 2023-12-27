# Classification Policy

<!--probably no longer needed-->

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
