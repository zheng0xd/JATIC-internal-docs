# Problem Statement

There is widespread interest across the DoD for capabilities to address the novel challenges posed by the T&E of AI. 

In this page, we outline some of the existing problems and consequent requirements.

## Previous limitations

While many AI T&E capabilities have been developed by previous DoD AI Programs, their usage throughout the Department has been limited by several key factors, including:

1. Lack of functionality for advanced AI T&E functions, such as robustness of bias testing
1. Lack of maturity, scalability, reproducibility, usability, or hardening of existing
1. Difficulty in deployment or use within DoD environments, including deployment into high-side environments
1. Difficulty in integration with MLOps pipelines different than the particular pipeline the capability was designed for
1. Difficulty in modular use alongside other tools from open-source or industry.
1. Inability for capabilities to evolve with developments in AI/ML research

These limitations, in addition to other factors, such as a lack of best practices for AI T&E, have inhibited the ability for DoD AI programs to perform sufficient T&E of their AI models.

## Documented need

The formal documented need for our program comes from the following sources:

1. *Responsible AI Strategy and Implementation Pathway*, issued by Deputy Secretary of Defense Kathleen Hicks in June 2022
1. *The National Artificial Intelligence Test & Evaluation Infrastructure Capability*, issued by CDAO in August 2023
1. *Executive Order on the Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence*, issued by President Joe Biden in October 2023

We will refer to these documents as the *RAI S&I Pathway*, the *NAITIC Report*, and the *AI Executive Order*, respectively. 

### RAI S&I Pathway

The RAI S&I Pathway document outlines a series of specific near-term steps for the implementation of the DoD's AI ethical principles and Responsible AI foundational tenets. Tenet 2 of the Pathway clearly defines the capability need that our program seeks to address. 

In particular, Tenet 2 charges the CDAO, in coordination with OUSD(R&E) and DOT&E, to execute the following:

!!! quote 

    LOE 2.1: BUILD A ROBUST TEVV ECOSYSTEM AND ACCOMPANYING INFRASTRUCTURE TO DEVELOP AND FIELD AI CAPABILITIES SAFELY AND SECURELY.

    LOE 2.1.1: Develop a TEW framework to articulate how test and evaluation (T&E) should be intertwined across an Al capability's lifecycle and pathways for continuous testing and standards for documentation and reporting. Identify synergies between AI T&E and traditional T&E (e.g. effectiveness, suitability, security, safety) to empower programs to streamline T&E efforts. Include guidance for operationalizing RAT principles into testable conjectures for common technologies, mission domains, and uses cases. 

    LOE 2.1.2: Develop or acquire Al-related T&E tools to be used as a resource for Al developers and testers. This AI T&E Toolkit shall draw upon best practices and innovative research from industry and the academic community, as well as commercially available technology where appropriate. The Toolkit will be made widely available to DoD users and shall include:

    1. Tangible, concrete guidance for PMs, testers, and other relevant T&E stakeholders about how to implement RAI T&E throughout a capability's lifecycle;
    2. T&E Master Plan template for AI and a set of templates for test plans;
    3. A library of T&E metrics for AI systems, including metrics for trustworthiness and confidence; and
    4. Necessary tools and technologies required to detect both natural degradation of and adversarial attacks on Al, including those to detect various attacks on AI systems, and that can notify testers or operators when such attacks are occurring. 

    LOE 2.1.3: Create a test range environment and central repository of tools for T&E of Al, linking to existing and emerging equivalent DoD Component environments, that enables easy and continuous testing for DoD testers. Where appropriate, tools that are housed in this environment should comply with DoD Enterprise DevSecOps Reference Designs for portability across the Department.

### NAITIC Report

The NAITIC Report was developed in response to the Fiscal Year 23 Program Decision Memorandum, in which the Deputy Secretary of Defense and the Office of Cost Assessment and Program Evaluation requested more information to support data-driven decisions about AI T&E infrastructure investments at the DoD enterprise level.

!!! quote 

    Program Decision Memorandum Terms of Reference (TOR)

    AI T&E capability is critical for responsible development and fielding of autonomous and artificial intelligence systems. DoD must target investments in this area at key gaps, leverage existing infrastructure in government, industry, and academia where possible, and ensure alignment of T&E investments at all levels—from the programs up to the enterprise—with a coherent vision. This study is essential to inform the decision space for AI T&E investments, and the TOR outlines criteria that will be used to evaluate the roadmap’s utility in this regard.

The report concluded that "[T]here is widespread interest for DoD enterprise-level T&E infrastructure to address the novel and exacerbated challenges posed by the T&E of AI. While programs are currently investing locally in T&E resources … there is still a consistent desire across survey programs for DoD enterprise support."

### AI Executive Order

The AI Executive Order recognized the extraordinary potential of AI and outlined a series of steps to ensure that our development and usage of the technology is safe and responsible. The below sections explicitly address the need for AI T&E and assurance capabilities to achieve this goal.

!!! quote

    Artificial Intelligence must be safe and secure. Meeting this goal requires robust, reliable, repeatable, and standardized evaluations of AI systems, as well as policies, institutions, and, as appropriate, other mechanisms to test, understand, and mitigate risks from these systems before they are put to use. It also requires addressing AI systems’ most pressing security risks—including with respect to biotechnology, cybersecurity, critical infrastructure, and other national security dangers—while navigating AI’s opacity and complexity. Testing and evaluations, including post-deployment performance monitoring, will help ensure that AI systems function as intended, are resilient against misuse or dangerous modifications, are ethically developed and operated in a secure manner, and are compliant with applicable Federal laws and policies. 

!!! quote

    Within 270 days of the date of this order, to help ensure the development of safe, secure, and trustworthy AI systems, the Secretary of Commerce, acting through the Director of the National Institute of Standards and Technology (NIST), in coordination with the Secretary of Energy, the Secretary of Homeland Security, and the heads of other relevant agencies as the Secretary of Commerce may deem appropriate, shall ...

    (B) in coordination with the Secretary of Energy and the Director of the National Science Foundation (NSF), developing and helping to ensure the availability of testing environments, such as testbeds, to support the development of safe, secure, and trustworthy AI technologies, as well as to support the design, development, and deployment of associated PETs, consistent with section 9(b) of this order. 
    