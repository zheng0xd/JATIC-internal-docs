# FAQ

## What is JATIC? Who operates it?
JATIC is a program started in 2023 with the goal of developing software products to accelerate AI Test and Evaluation (T&E) practices and provide rigorous assurance of the effectiveness, safety, and robustness of AI-enabled systems. The JATIC program is managed by the Assessment & Assurance Division of the Chief Digital and Artificial Intelligence Office ([CDAO](https://www.ai.mil/)) within the Department of Defense (DoD).

JATIC provides several categories of software products aimed at AI T&E including python libraries scoped to specific aspects of AI T&E, a software framework that allows for a T&E workflow comprised of an interoperable set of products, and an AI T&E platform. These open-source products are designed as a set of interoperable building blocks that are easy to use at the enterprise level without vendor lock-in. 

## What do you mean by AI Test & Evaluation (T&E)?
CDAO is creating a framework (link) to provide best practices and guidance on how to test and evaluate an AI or AI-enabled system across its lifecycle. This sequential T&E process includes examination of the AI models and their corresponding data, as well as examining the model’s integration into a wider system, performance in operational settings, and ability to integrate with humans. JATIC’s focus is on the evaluation of the models themselves, known as the AI algorithm or AI model T&E.

With this focus on AI algorithm T&E, JATIC products can be applied across multiple missions and systems even with a limited amount of domain knowledge.

## Will JATIC be maintained long-term? 
Yes! JATIC is funded from fiscal year 2023-2029 (FY23-29) in order to develop and sustain open-source products for AI T&E.

## How can I access JATIC products? Where are they hosted?
If you are a government employee or contractor, you can use your email to sign up for an account at [gitlab.jatic.net](gitlab.jatic.net) to access any of the free JATIC products.

Many JATIC products will also be publicly released and open-sourced on GitHub, Conda, and PyPi.

Additionally, JATIC is targeting multiple hosting locations on different DoD library repositories such as Repo1 and IronBank.

## Why should I use JATIC products?
All of our products are interoperable, meaning they adhere to common protocols in order to work naturally with each other and with common Machine Learning (ML) frameworks and Machine Learning Operations (MLOps) platforms. Our products are mature, well-documented and secure, primed for enterprise deployment across environments at various classification levels. Outputs from our products are also validated to support high-consequence T&E activities.

We emphasize accessibility and usability with every JATIC product, allowing users with limited AI/ML experience to quickly come up to speed on our products and fine-tune the settings as they learn more.

Finally, JATIC products make use of and build upon state-of-the-art products and metrics across the open-source community. All products designed by JATIC are free for government organizations & their contractors to use and many will also be open-sourced and freely available to the broader AI community.

## Are there specific use cases JATIC is focused on?
Yes, JATIC’s initial focus is on Computer Vision Classification & Object Detection. Future expansion efforts will include other modalities, data, and problems, including large language models (LLMs).

## Who are the target personas for JATIC?
Our target personas currently include an AI/ML test & evaluation engineer, a data scientist or researcher, and an AI/ML engineer.

## What AI T&E capabilities does JATIC support?
JATIC’s software libraries currently support AI T&E capabilities to assess model performance, robustness against adversarial attacks, robustness against natural perturbations and explainability; to analyze capabilities and limitations of models, datasets and labels; and to generate model cards, data cards, and test reports.

JATIC is always looking for high-value products to build or bring into the program, so please [contact us](cdao-jatic@groups.mail.mil) with ideas on addressing additional AI T&E capabilities. 

## What AI T&E capabilities does JATIC NOT support or provide?
JATIC does not recreate functionality for many foundational capabilities often found within an MLOps pipeline such as dashboards, experiment tracking, or workflow orchestration. Instead, JATIC leans on existing capabilities from open-source. This modularity allows JATIC tools to easily integrate into a wide variety of existing MLOps stacks.

## Does JATIC provide models or datasets? 
No. However, we do provide examples of models/datasets acquired from open-source repositories that may be analogous to real operational data.

## Does JATIC provide metrics? 
Yes! JATIC provides a range of metrics that cover the general (e.g. accuracy, mean average precision) and the highly specific (e.g. irreducible error, dataset distance).

## How should I do T&E with JATIC products?
Sufficient testing for a given AI model ultimately needs to be tailored for the specific mission and workflow in which the model will operate. JATIC provides a set of building blocks that you can use to create a multi-faceted algorithm test to measure the performance, reliability, robustness, and explainability of an AI model.

## How can I integrate JATIC products into my T&E?
JATIC tools are specifically designed for easy integration into existing T&E workflows or Machine Learning Operations (MLOps) pipelines. 

Organizations who have already adopted an enterprise MLOps platform such as Databricks or Sagemaker can integrate the JATIC python libraries directly into their existing infrastructure. Organizations without that infrastructure can use JATIC’s AI T&E Platform – RAVEN – to set up a T&E and development platform.

## Will using JATIC products in my T&E process provide certification/accreditation for my program?
Not currently. However, the use of JATIC products may help provide the necessary documentation required for certain DoD processes such as DoD Directive 3000.09.

## Will JATIC do the verification/T&E for me? Will JATIC design my T&E? 
No, we believe that mission owners and T&E engineers within the mission space are best equipped to design and execute the testing of their own AI-enabled systems given their detailed understanding of the requirements, risks, and operational conditions of their mission.

The CDAO AI T&E framework (link) provides guidance on unique considerations for the T&E of AI-enabled systems.

## Can I use JATIC products on classified systems or data?
Yes! JATIC products will be hardened and secured for straightforward deployment into high-side environments. We are actively working on improvements to harden our current products, so please [reach out](cdao-jatic@groups.mail.mil) if you would like assistance with bringing JATIC products into your environment.

## Will JATIC collect my testing data or results?
No, JATIC will never collect testing data or results.

## My AI task/domain isn’t discussed in current JATIC materials. Can I still use the JATIC tools?

While our JATIC products may not currently be applicable to your other AI task or domain, please contact us to provide additional information about your T&E needs. JATIC is constantly evolving and we’d appreciate [your feedback](https://forms.osi.apps.mil/pages/responsepage.aspx?id=kQEtEK7uYUexyxqD6G70RffprThOa3hKghVjeesZps5UN1hXMDUxN1dXM0c3SUJZVE1FMU1PTDAyQi4u) on use cases we could consider in the future.

## How do I follow up with JATIC?
- To begin using the products: [Create an account or login to GitLab](https://gitlab.jatic.net/)
- To watch recordings of demos or deep dives: [Click here](https://jatic.pages.jatic.net/internal-docs/presentations/) 
- To sign up for emails: [Complete our interest form](https://forms.osi.apps.mil/pages/responsepage.aspx?id=kQEtEK7uYUexyxqD6G70RffprThOa3hKghVjeesZps5UN1hXMDUxN1dXM0c3SUJZVE1FMU1PTDAyQi4u)
- To provide feedback on a product or ask questions: [Send us an email](cdao-jatic@groups.mail.mil)
- To contribute to JATIC products: [Send us an email](cdao-jatic@groups.mail.mil)
- To learn more about AI T&E: View CDAO's T&E frameworks

