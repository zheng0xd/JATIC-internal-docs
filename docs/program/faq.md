# FAQ

## What is JATIC? Who operates it?

JATIC is a program started in 2023 with the goal of developing software products to accelerate AI Test and Evaluation (T&E) practices and provide rigorous assurance of the effectiveness, safety, and robustness of AI-enabled systems. It is managed by the Assessment & Assurance Division of the Chief Digital and Artificial Intelligence Office ([CDAO](https://www.ai.mil/)) within the Department of Defense (DoD).

The program provides several software products aimed at enhancing AI T&E. These  products are designed as a set of interoperable building blocks that are easy to use at the enterprise-level without vendor lock-in.

## What do you mean by AI Test & Evaluation (T&E)?

!!! warning

    needs editing

CDAO is creating a framework (link) to provide best practices and guidance on how to test and evaluate an AI or AI-enabled system across its lifecycle. This sequential T&E process includes examination of the AI models and their corresponding data, as well as examining the model’s integration into a wider system, performance in operational settings, and ability to integrate with humans. JATIC’s focus is on the evaluation of the models themselves, known as the AI algorithm or AI model T&E.

With this focus on AI algorithm T&E, JATIC products can be applied across multiple missions and systems even with a limited amount of domain knowledge.

## Will JATIC be maintained long-term?

Yes! The program is funded to develop and sustain software products for AI T&E.

## How can I access JATIC products?

Many products developed within the program are available as open-source software which can be downloaded from GitHub, Conda, and PyPi.

Additionally, all government employees or contractors can sign up for accounts at [gitlab.jatic.net](gitlab.jatic.net) to access the full suite of software products. Finally, the program is targeting multiple hosting locations on different DoD library repositories such as Repo1 and IronBank.

## Why should I use JATIC products?

All of products developed within the JATIC program are interoperable, meaning they adhere to common protocols in order to work naturally with each other and with common Machine Learning (ML) frameworks and Machine Learning Operations (MLOps) platforms. Our products are mature, well-documented and secure, primed for enterprise deployment across environments at various classification levels. Outputs from our products are also validated to support high-consequence T&E activities.

We emphasize accessibility and usability with every JATIC product, allowing users with limited AI/ML experience to quickly come up to speed on our products and fine-tune the settings as they learn more.

Finally, JATIC products make use of and build upon state-of-the-art products and metrics across the open-source community. All products designed by JATIC are free for government organizations & their contractors to use and many will also be open-sourced and freely available to the broader AI community.

## Are there specific use cases JATIC is focused on?

Yes, our initial focus is on Computer Vision Classification & Object Detection. Future expansion efforts will include other modalities, data, and problems, including large language models (LLMs).

## Who are the target personas for JATIC?

Our target personas currently include an AI/ML test & evaluation engineer, a data scientist, and an AI/ML engineer.

## What AI T&E capabilities does JATIC support?

Our software libraries currently support AI T&E capabilities to assess model performance, robustness against adversarial attacks, robustness against natural perturbations and explainability; to analyze capabilities and limitations of models, datasets and labels; and to generate model cards, data cards, and test reports.

We are always looking for high-value products to build or bring into the program, so please [contact us](cdao-jatic@groups.mail.mil) with ideas on addressing additional AI T&E capabilities.

## What AI T&E capabilities does JATIC NOT support or provide?

We do not recreate functionality for many foundational capabilities often found within an MLOps pipeline such as dashboards, experiment tracking, or workflow orchestration. Instead, we leans on existing capabilities from open-source. This modularity allows our products to easily integrate into a wide variety of existing MLOps stacks.

## Does JATIC provide models or datasets?

No. However, we do provide examples of models/datasets acquired from open-source repositories that may be analogous to real operational data.

## Does JATIC provide metrics?

Yes! We provide a range of metrics that cover the general (e.g. accuracy, mean average precision) and the highly specific (e.g. irreducible error, dataset distance).

## How should I do T&E with JATIC products?

Sufficient testing for a given AI model ultimately needs to be tailored for the specific mission and workflow in which the model will operate. We aim to provide a set of building blocks that you can use to create a multi-faceted algorithm test to measure the performance, reliability, robustness, and explainability of an AI model.

## How can I integrate JATIC products into my T&E?

Our products are are specifically designed for easy integration into existing T&E workflows or Machine Learning Operations (MLOps) pipelines.

Organizations who have already adopted an enterprise MLOps platform such as Databricks or Sagemaker can integrate the JATIC python libraries directly into their existing infrastructure. Organizations without that infrastructure can leverage RAVEN to set up a T&E and development platform.

## Will using JATIC products in my T&E process provide certification/accreditation for my program?

Not currently. However, the use of JATIC products may help provide the necessary documentation required for certain DoD processes such as DoD Directive 3000.09.

## Will JATIC do the verification/T&E for me? Will JATIC design my T&E?

!!! warning

    needs editing

No, we believe that mission owners and T&E engineers within the mission space are best equipped to design and execute the testing of their own AI-enabled systems given their detailed understanding of the requirements, risks, and operational conditions of their mission.

The CDAO AI T&E framework (link) provides guidance on unique considerations for the T&E of AI-enabled systems.

## Can I use JATIC products on classified systems or data?

Yes! Our products will be hardened and secured for straightforward deployment into high-side environments. We are actively working on improvements to harden our current products, so please [reach out](cdao-jatic@groups.mail.mil) if you would like assistance with bringing them into your environment.

## Will JATIC collect my testing data or results?

No, our products will never collect any telemetry, including testing data or results.

## My AI task/domain isn’t discussed in current JATIC materials. Can I still use the JATIC products?

While our products may not currently be applicable to your other AI task or domain, please contact us to provide additional information about your T&E needs. Our program is constantly evolving and we’d appreciate [your feedback](https://forms.osi.apps.mil/pages/responsepage.aspx?id=kQEtEK7uYUexyxqD6G70RffprThOa3hKghVjeesZps5UN1hXMDUxN1dXM0c3SUJZVE1FMU1PTDAyQi4u) on use cases we could consider in the future.

## How do I follow up with JATIC?

- To begin using the products: [Create an account or login to GitLab](https://gitlab.jatic.net/)
- To watch recordings of demos or deep dives: [Click here](https://jatic.pages.jatic.net/internal-docs/presentations/) 
- To sign up for emails: [Complete our interest form](https://forms.osi.apps.mil/pages/responsepage.aspx?id=kQEtEK7uYUexyxqD6G70RffprThOa3hKghVjeesZps5UN1hXMDUxN1dXM0c3SUJZVE1FMU1PTDAyQi4u)
- To provide feedback on a product or ask questions: [Send us an email](cdao-jatic@groups.mail.mil)
- To contribute to JATIC products: [Send us an email](cdao-jatic@groups.mail.mil)
- To learn more about AI T&E: View CDAO's T&E frameworks
