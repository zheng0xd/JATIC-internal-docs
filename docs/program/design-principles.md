# Design Principles

Before adopting any JATIC products, its good to understand the design principles behind the program and ensure they align with your goals. This page explains the design principles by which products within the program are chosen and developed.

## Core design principles

- **Wide interoperability**: Our products work naturally with each other, with common ML frameworks, and with common MLOps platforms.
- **Standalone and modular**: Each product is usable independently, but also fits within a larger, compatible, and modular tool suite.
- **Straightforward deployment**: Users can easily deploy our products into their own environments at various classification levels, whether they are local machines, on-prem servers, cloud servers, or HPC.
- **Extremely accessible and easy-to-use**: Users with limited AI/ML experience can quickly come up to speed on our products, enabled by excellent documentation and highly usable software.
- **Useful defaults**: Useful default settings allow users to quickly get started and fine-tune as they learn more.
- **Mature, stable, and secure**: Our products bring high levels of software maturity, stability, and security in order to be used within enterprise settings.
- **Validated**: Functionality from our products is validated in order to support high-consequence T&E activities.
- **Open-source**: Our products heavily make use of, build upon, and contribute to the open-source community. They are available freely with open-source licenses. No vendor lock-in, no reinventing the wheel.

*[HPC]: High-Performance Computing

!!! warning

    Some of these design principles are aspirational! There are current products within the program that fail to meet some of these criteria. 

## Python library design principles

Many of the products developed within the program are python libraries which additionally adhere to the following design principle:

- **Narrow scope of functionality**: Each library has a narrow scope of functionality which is restricted to a particular AI T&E function, allowing easy integration into sophisticated and tailored pipelines.

With heavy use of open-source, narrow functionality, and a lightweight form factor, these libraries are sufficiently flexible to be used across many different AI T&E workflows, ML technology stacks, and computing environments.

!!! note

    Due to their narrow scope, these libraries may be applicable to many other stages of the ML lifecycle besides T&E, such as model development or post-deployment monitoring.
