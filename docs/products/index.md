# Products

The program creates two categories of products.

## AI T&E python libraries



## RAVEN - AI T&E platform

## AI Assurance Toolbox

By limiting the software form factor to python libraries, a narrow scope of functionality, and heavy re-use of open-source, this toolbox will be sufficiently flexible to be easily usable within many different T&E workflows, ML technology stacks, and compute environments. For instance, individual libraries within the AI Assurance Toolbox will be usable independently within Jupyter Notebooks to enable quick model testing and metrics visualization (e.g., gradio, streamlit), and also within production-level ML pipelines - leveraging features such as test automation, experiment tracking, and visualization dashboards - to enable powerful new insights into model performance.

In addition, while JATIC is primarily focused on supporting T&E of models after training, the libraries within the AI Assurance Toolbox will be applicable to many other phases of the AI lifecycle, such as model development or post-deployment monitoring.

## AI T&E Platform

We noted above how libraries within the AI Assurance Toolbox are sufficiently flexible to be used within many AI/ML platforms, given their lightweight form factor and narrow scope. However, some common MLOp capabilities such as automation, tracking, and visualization are critical components for any AI T&E pipeline. By not providing this functionality in the AI Assurance Toolbox (as to not duplicate effort which exists in many MLOps platforms), it becomes very hard for users without an existing platform or pipeline (which we call "platform-free" users in the Design Principles) to use these tools to their full potential - the libraries will seem fragmented and disconnected.

For these users, the AI Assurance Toolbox may be delivered altogether, bundled together with open-source, industry-standard tools for workflow automation, experiment tracking, object storage, visualization, etc. This will provide a comprehensive and opinionated platform for AI T&E, which may either be adopted wholesale or used as a reference architecture. We call this platform the **AI T&E Platform**. 

The AI T&E Platform will be deployable to a Kubernetes cluster on commercial cloud (AWS, Azure primary targets) or on-prem. Additionally, it will be deployable to local machines as a set of dockerized micro-services. It will enable the use of infrastructure as code to quickly be deployable to a diverse set of environments.

