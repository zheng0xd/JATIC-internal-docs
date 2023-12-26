# Supported Applications

The program is currently focused on developing AI T&E capabilities to test AI models for computer vision (CV) classification and object detection (OD) tasks. 

The libraries and tools that the program are building are designed to be applicable across domains and missions that employ these types of AI algorithms. In particular, the primary mission use cases which we are focused on are:

1. Satellite imagery
1. UAV imagery
1. Autonomous driving

These do not preclude application to other tasks, but serve as the primary missions that guide our development.

!!! info

    For each of the above missions, we work closely with DoD mission-owners to understand their requirements and integrate our products into their T&E workflows. 
    
    For each of the above, we also select a representative open-source dataset to serve as our target which we use within development and demonstrations. 

## Rationale

### For focusing on computer vision

CV classification and OD were chosen as the initial AI tasks for the program due to their wide use use across the DoD in many diverse operational contexts, including satellite imagery, medical imagery, and object detection on UAVs, and autonomous vehicles. 

Throughout these operational contexts, the underlying AI models often had very similar underlying architectures, which suggested the possibility of a common set of tools to test across these domains.

### For limiting to AI model testing 

The program limits its scope to AI model testing. While other areas of T&E, such as systems integration, human-system integration, and operational T&E are complex issues with critical capabilities gaps, particularly for AI-enabled systems, they are out of scope for the program. 

Other areas of testing, such as systems integration testing, are far more difficult to develop generalizable T&E capabilities for. For example, while the same T&E software may be able to test a CV model for radiology and a CV model for vehicle detection on UAVs, the required systems integration testing for these two capabilities looks completely different. Thus, we believe that capabilities for systems integration, human-system integration, and operational T&E should be left to individual organizations, agencies, and services to develop, who themselves have the best insight into their operational mission and systems.

## Other AI modalities

The program may create products for AI T&E within other AI modalities, such as natural language processing or generative AI, in its future years. The priority of each of these modalities is not fixed and will continue to evolve as CDAO gets clearer demand signals from the DoD on its AI T&E capability gaps.

Currently, the overhead of supporting multiple AI modalities is too large to justify. This overhead includes supporting a divergent user base and spreading out our market research across multiple modalities.
