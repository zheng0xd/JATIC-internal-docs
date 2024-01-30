# Frequently Asked Questions

## What functionalities and metrics do JATIC products provide?

We provide functionality for:

1. assessing model performance, explainability, and robustness against adversarial and natural perturbations
1. assessing dataset similarity, difficulty, and label accuracy
1. generating model cards, data cards, and test reports

To accomplish this, we provide a variety of metrics, ranging from standard metrics, such as accuracy and mean average precision, to task-specific metrics, such as Henze-Penrose divergence for measuring distance between datasets.

## What functionalities do JATIC products NOT provide?

We do not provide or recreate common MLOps functions such as model registries, object storage, dashboards, experiment trackers, or workflow orchestrators. This enables our products to integrate easily into a wide variety of existing MLOps platforms.

## How can I access JATIC products?

Most products developed within the program are available as open-source software which can be downloaded from public platforms such as GitHub, Conda, and PyPi. See [**Products**](../products.md) for all of our publicly released software.

Additionally, all government employees or contractors can sign up for accounts at [https://gitlab.jatic.net](https://gitlab.jatic.net) to access the full suite of software products.

## Can JATIC products be used on classified systems or data?

Yes, our products are hardened and secured to enable straightforward deployment into high-side environments.

!!! note

    We are actively working on improvements to harden our current products, so please reach out at [cdao-jatic@groups.mail.mil](mailto:cdao-jatic@groups.mail.mil) if you would like assistance bringing them into your environment.

## Does the JATIC program perform AI test and evaluation on specific programs?

No, we believe that test engineers within the mission space are best equipped to design and execute the testing of their systems — given their detailed understanding of the requirements, risks, and operational conditions of their mission.

!!! note

    While we do not perform testing, we are happy to support deployment of our products into your environment and provide guidance on the T&E of AI-enabled systems. Please reach out at [cdao-jatic@groups.mail.mil](mailto:cdao-jatic@groups.mail.mil) to discuss!

## Does the JATIC program provide datasets for AI test and evaluation?

No, we do not provide datasets for AI test and evaluation. However, we do provide tutorials and demonstrations of our products used with open-source datasets which may be instructive for testing with operational data.

## Will JATIC products provide accreditation for my system?

No, the use of our products within your testing and evaluation will not currently provide any certification or accreditation. However, they may help provide the necessary documentation required for certain DoD processes such as DoD Directive 3000.09.

## Will JATIC products be continually updated and sustained?

Yes, our program is funded to develop, update, and sustain its software products — especially as AI technology continues to advance.

## Will JATIC products collect my testing data or results?

No, our products will never collect any telemetry, including testing data or results.
