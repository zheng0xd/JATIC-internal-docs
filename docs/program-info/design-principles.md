# Design Principles

This page explains the design principles by which products within the program are chosen and developed.

- **Wide interoperability**: Our products work naturally with each other, with common ML frameworks, and with common MLOps platforms.
- **Straightforward deployment**: Users can easily deploy our products into their own environments at various classification levels, whether they are local machines, on-prem servers, cloud servers, or HPCs. 

*[HPC]: High-Performance Computing

- **Extremely accessible and easy-to-use**: Technical users with limited AI/ML experience can quickly come up to speed on our products, enabled by excellent documentation and highly usable software.
- **Stable, mature, and secure**: Our products bring high levels of software stability, maturity, and security in order to be used within enterprise settings.
- **Validated**: Outputs from our products are validated in order to be used to support high-consequence T&E activities.
- **Open-source**: Our products both build upon and contribute to the open-source community. No licenses, no vendor lock-in, no reinventing the wheel.

!!! warning

    Some of these design principles are aspirational! There are current products within the program that fail to meet some of these criteria. 

## Python libraries

Most of the software developed within the JATIC program in FY23 will fall within the **AI Assurance Toolbox**.

This toolbox will be a set of python libraries, mutually compatable, built on a set of shared design principles, with a narrowly scoped set of functionality specific to AI T&E.

Tools within the AI Assurance Toolbox will generally adhere to the following principles:

- Will be usable as independent but mutually compatabible python libraries
- Will prefer a narrow scope of functionality constrained to AI T&E, making use of existing open-source solutions for common ML tasks like data loading, experiment tracking, visualization, model inference, etc.
- Will implement open-source standard APIs for models, datasets, etc.
- Will build upon existing open-source libraries (especially when the open-source components are widely used and recognized), increasing their maturity, compatibility, or relevancy for DoD usage
- Will (where appropriate) publically release or open-source capabilities
- Will be designed to enable straightforward contributions from developers in the community
- Will be designed to enable continual evolution with the state-of-the-art in AI T&E and updates in ML technologies
- Will allow users to add functions (e.g., custom metrics, perturbations, adversarial attacks) in an extensible way
- Will be lightweight and straightforward to run on a wide range of deployment environments, including all major operating systems, cloud deployments, etc.
- Will be comprhensively supported with examples, tutorials, and documentation

By limiting the software form factor to python libraries, a narrow scope of functionality, and heavy re-use of open-source, this toolbox will be sufficiently flexible to be easily usable within many different T&E workflows, ML technology stacks, and compute environments. For instance, individual libraries within the AI Assurance Toolbox will be usable independently within Jupyter Notebooks to enable quick model testing and metrics visualization (e.g., gradio, streamlit), and also within production-level ML pipelines - leveraging features such as test automation, experiment tracking, and visualization dashboards - to enable powerful new insights into model performance.

In addition, while JATIC is primarily focused on supporting T&E of models after training, the libraries within the AI Assurance Toolbox will be applicable to many other phases of the AI lifecycle, such as model development or post-deployment monitoring.

## Platform

We noted above how libraries within the AI Assurance Toolbox are sufficiently flexible to be used within many AI/ML platforms, given their lightweight form factor and narrow scope. However, some common MLOp capabilities such as automation, tracking, and visualization are critical components for any AI T&E pipeline. By not providing this functionality in the AI Assurance Toolbox (as to not duplicate effort which exists in many MLOps platforms), it becomes very hard for users without an existing platform or pipeline (which we call "platform-free" users in the Design Principles) to use these tools to their full potential - the libraries will seem fragmented and disconnected.

For these users, the AI Assurance Toolbox may be delivered altogether, bundled together with open-source, industry-standard tools for workflow automation, experiment tracking, object storage, visualization, etc. This will provide a comprehensive and opinionated platform for AI T&E, which may either be adopted wholesale or used as a reference architecture. We call this platform the **AI T&E Platform**. 

The AI T&E Platform will be deployable to a Kubernetes cluster on commercial cloud (AWS, Azure primary targets) or on-prem. Additionally, it will be deployable to local machines as a set of dockerized micro-services. It will enable the use of infrastructure as code to quickly be deployable to a diverse set of envrionments.
