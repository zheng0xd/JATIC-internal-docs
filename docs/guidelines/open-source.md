# Open-sourcing Guidelines

This page outlines a general policy towards public release, open-source, and open-collaboration for our program. It outlines the situations where open-source or public release of features are desirable, and the situations where they are not. 

Because of the numerous products within the program and their diverse development histories, we **does not** provide a technical and detailed guide on the management of public and internal versions. Each product is expected to create a detailed release strategy for their product, which should detail management of public and internal features.


## Definitions

For clarity, we define some related but distinct terms.

- We say that a project is **publicly released** when its software has been approved and released to the open internet.
- We say that a project is **open-source** when its software and its source code have been approved and released to the open internet with a license that allows any user to use, change, and re-distribute the source code without restriction. 
- We say that a project is **open-collaboration** when its software and its source code have been approved and released to the open internet, and has a policy which allows any capable internet user to participate in its development. 

Note that a project can be public release without being open-source, for example, if it has a license that restricts commercial and military use. A project can also be open-source without being open-collaboration, if it does not, in practice, accept external contributions requests.

## Overall objectives

The program aims to use public release, open-source, and open-collaboration to achieve the following objectives:

1. get new features in front of as many users as quickly as possible
1. allow products to be distributed as easily and as widely as possible
1. maintain compatibility and relevancy with other products
1. reduce bugs by getting more eyes on the code
1. increase trust and transparency of products
1. increase adoption of open and common standards 
1. get feedback and contributions from the larger AI community
1. establish positive DoD and CDAO image within the space

On the other hand, there are situations where public release, open-source, and open-collaboration is not appropriate and may:

1. reduce comparative national security advantage
1. reduce industry competitive incentives
1. provide potential for malicious contributions

Case-by-case determinations of public release and open-source will attempt to strike a balance between these factors. 

**In general, we would like to publicly release, open-source, and allow open-collaboration on as much of what we develop within the program as possible.** 

Some products may need to maintain a publicly released version, as well as modules that are kept internal for DoD use. The most common instance where this is not possible will be when a feature is directly requested by a DoD organization and is uniquely relevant to their mission application. In cases like these, we would like to develop a project construct which allows us to still achieve the benefits of public release for the rest of the capability.

!!! example

    An external DoD organization has developed a set of adversarial techniques which they would like incorporated into the program, but not publicly released. 

    In this case, we may develop a private module for these new techniques that extends the publicly released main library.

## Choosing a license

For products that are publicly released, it is preferable that they use licenses which are conducive to the above objectives.

If there is opportunity to choose a license for a new product (for instance, if the product began within the program, or previously has never been previously released externally), a discussion on the license should be held between the development team, the government, and the product owner.

Permissive licenses such as Apache, MIT, or BSD are preferred. 

## Public release / open-source process

There are provisions within many of the existing contracts for the developing companies to release code without any explicit approval from the government. Within these contracts, the government has the responsibility of explicitly denying the release of certain features if they would not like them to be publicly released. Within other contracts where the government has not given this approval to the developing companies, the code will be pushed through the government public release process.

In both cases, it is the responsibility of the government and product owners to determine **during increment planning** if there are any particular features that will be developed during the increment which cannot be publicly released and open-sourced. For these features, a technical plan shall be created to ensure that these features can be developed in an extensible module, or that the branch with these features will otherwise still be able to pull from future developments in the upstream open-source branches.

The government reserves the right to determine at any point if a feature cannot be publicly released or open-sourced. For instance, this may occur in the case where there are significant changes from the increment goals during execution. This should be a rare exception.

## Synchronization with upstream open-source branches

Many projects will have significant development external to the project's development within the program. This may be development by other parts of the company, or developments from the open internet.

Please follow these two principles when synchronizing with other versions or branches.

- It is important to facilitate easy synchronization with upstream developments, since this provides access to valuable developments from the larger community.
- Code should be tested for correct behavior and security before accepting any pull requests, particularly from outside the program.

## Project-specific release strategies

This page does not provide specific guidance on the details, technical processes, or schedule to follow for public release or open-source. 

**Each project must create a release strategy that documents the particular details for their project. This document must be approved by the program prior to any public releases of the project.**

At the very least, this document should discuss:
- general strategy for public release, open-source, and open-collaboration
- internal and public release cadence 
- target platforms for public release, open-source, and open-collaboration
- strategy for synchronization with upstream versions or branches
- strategy for reviewing pull requests from internet
- type of open-source license which the project will use

Each project should also create a `CONTRIBUTING.md`, use git hooks to enforce style, set up security testing in CI, etc. Please briefly include these details in the release strategy.

This release strategy should build upon the [TBD program's overall release strategy](./Branch,%20Merge,%20Release%20Strategy.md). It will likely look different between the various projects. For some, it may be a continuous deployment of the features into the public version, with the public and internal version looking identical with repo [mirroring](https://docs.gitlab.com/ee/user/project/repository/mirror/index.html). For others, the public release may happen at a much slower release cadence.
