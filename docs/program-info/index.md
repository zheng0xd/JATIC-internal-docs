# About the program

The Joint AI T&E Infrastructure Capability (JATIC) program develops software products for AI Test & Evaluation (T&E) and AI Assurance. 

We aim to provide products that address the following key gaps:

- Resilience, robustness, and explainability of AI models
- Reproducibility and traceability of AI experiments
- Interoperability, security, and maturity of AI T&E software
- Documentation and ease-of-use for DoD testers

The program is managed by the Assessment & Assurance Division of the DoD Chief Digital and Artificial Intelligence Office (CDAO). It is funded from funded from FY23-FY29.

## Objectives and vision

Develop AI T&E tools that are widely adopted by DoD programs to increase the rigor of their missions and by the open-source community

Increase the speed and rigor of AI model T&E across the DoD

## Problem statement

There is widespread interest throughout the DoD for enterprise-level T&E capabilities to address the novel challenges posed by the T&E of AI. While many T&E capabilities have been developed by previous DoD AI Programs to meet the specific needs of those programs, their usage and distribution throughout the Department has been limited by several key factors, including:

1. Lack of capabilities for advanced AI T&E functions, such as robustness testing.
2. Lack of maturity, scalability, reproducibility, ease of use, or cyber-hardening of capabilities.
3. Difficulty deploying and using capabilities within DoD environments.
4. Difficulty using capabilities within ML pipelines and technology stacks.
5. Difficulty using capabilities in an integrated T&E pipeline, as each individual capability often requires custom model formats or data wrangling.
6. Inability for capabilities to evolve with developments in AI research.

These limitations, in addition to other factors, such as a lack of common standards and best practices for AI T&E, have inhibited the ability for DoD AI programs to perform comprehensive T&E of their AI models.

A further discussion of previous AI T&E capabilities can be found in JATIC Design Principles.

In addition previous capabilities were also greatly limited by the T&E functions that they enabled users to perform and were primarily limited to producing summary metrics of the performance of an AI model over an entire dataset. With only these functions it is difficult to understand the functioning of an AI model in operation.

It is not clear that a test dataset is well representative of an operational dataset, or that there are no biases in the test dataset. Even if an AI model does well overall across a test dataset, that does not indicate that it is free of biases or performance variations across the subclasses. It also does not indicate that it is robust to operationally realistic perturbations or adversarial attacks. Finally, understanding the overall performance of a model does not provide sufficient intuition for what features a model finds important or what criteria it is using to make its decision. Possessing these additional capabilities and more greatly strengthens the ability for a tester or analyst to understand the performance of an AI model.
