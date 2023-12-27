# Design Principles

This page explains the design principles by which products within the program are chosen and developed.

## Overall design principles

- **Wide interoperability**: Our products work naturally with each other, with common ML frameworks, and with common MLOps platforms.
- **Straightforward deployment**: Users can easily deploy our products into their own environments at various classification levels, whether they are local machines, on-prem servers, cloud servers, or HPC. 
- **Extremely accessible and easy-to-use**: Technical users with limited AI/ML experience can quickly come up to speed on our products, enabled by excellent documentation and highly usable software.
- **Stable, mature, and secure**: Our products bring high levels of software stability, maturity, and security in order to be used within enterprise settings.
- **Validated**: Outputs from our products are validated in order to be used to support high-consequence T&E activities.
- **Open-source**: Our products heavily make use of, build upon, and contribute to the open-source community. They are available freely with open-source licenses. No vendor lock-in, no reinventing the wheel. 
- **Standalone but mutually compatible**: Each product is usable independently, but also fits within a larger compatible tool suite.

*[HPC]: High-Performance Computing

!!! warning

    Some of these design principles are aspirational! There are current products within the program that fail to meet some of these criteria. 

## For python libraries

Many of the products developed within the program are python libraries which additionally adhere to the following design principle:

- **Narrow scope of functionality**: Each library has a narrow scope of functionality which is restricted to a particular AI T&E function, allowing easy integration and modularity

With heavy use of open-source, narrow functionality, and a lightweight form factor, these libraries are sufficiently flexible to be used across many different AI T&E workflows, ML technology stacks, and computing environments.

!!! note

    Due to their narrow scope, these libraries may be applicable to many other stages of the ML lifecycle besides T&E, such as model development or post-deployment monitoring.
