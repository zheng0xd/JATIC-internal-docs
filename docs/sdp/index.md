# Software Requirements

The software requirements can roughly be described as "follow the software development plan (SDP)".
The SDP classifies its requirements for clarity, [per the classifications](../reqs/index.md#requirement-classification). 

## Software Development Plan (SDP)

The software development plan (SDP) describes the software requirements for the development of software within the JATIC program. It includes approach, standards, expectations, and recommendations. All content is classified according to [the requirements classifications](../reqs/index.md#requirement-classification). 

### SDP Organization

The SDP is organized as follows:

- **[Common Protocols](./protocols.md)**
- **[Software Requirements](./software-requirements.md)**
- **[Testing Requirements](./testing-plan.md)**
- **[DevSecOps Requirements](./devsecops.md)**
- **[Branch, Merge, and Release Requirements](./branch-merge-release.md)**

### Philosphy

The SDP is designed with three types of stakeholders in mind: 

- developers of JATIC tools
- end-users of JATIC tools
- JATIC program organizers

#### Developers of JATIC tools

The SDP provides to **developers of JATIC tools** clear requirements to meet program expectations. 
These requirements are intended to be reasonable and feasible. They are meant to provide some guardrails against poor development practices and poor final products. They are also meant to ensure some level of consistency across tools created by our program. Some of the requirements are simply "opinions", a choice between several good options for consistency.

!!! info 

    The requirements can be changed. If any requirements seem wrong, infeasible, poorly chosen, overly difficult to adhere to, or otherwise cause strife, let program management know. Adding options for requirements is a common response to such issues.

Some requirements in the SDP are designed to meet acceptance criteria from users. For example, security-related testing requirements may be necessary for users whose intended environment for use of JATIC tools has security requirements.

Adherence to the SDP should simplify the process of creating high-quality Python projects, and provide opinions to eliminate the need to choose from the many different approaches to packaging, testing, documentation, etc. It will also ease integration efforts between development teams through consistency in code and practice. 

#### End-users of JATIC tools

The SDP provides to **end-users of JATIC tools**, information about consistent requirements that all JATIC tools meet. This allows users to make informed decisions relating to use of the tools. The SDP contains technical details related to security, testing, coding, and processes that may or may not meet user requirements. Compliance by development teams with the SDP should improve quality and consistency of tools, which will improve user experience with the tools.

#### JATIC program organizers

**JATIC program organizers** include program management as well as others who work to organize program-wide cohesive work. The SDP provides to **JATIC program organizers** understanding of requirements met by each team. Compliance by development teams with the SDP will improve consistency in code and practice. Program organizers will use the SDP as reference for evaluation of compliance with program requirements in technical reviews. The SDP will be used to update and automate the enforcement of requirements in a way that is both systematic and scalable.
