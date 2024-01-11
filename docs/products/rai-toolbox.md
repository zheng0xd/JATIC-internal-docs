---
hide:
- navigation
---

# Responsible AI Toolbox

The rAI-toolbox is designed to enable methods for evaluating and enhancing both the robustness and the explainability of artificial intelligence (AI) and machine learning (ML) models in a way that is scalable and that composes naturally with other popular ML frameworks.

A key design principle of the rAI-toolbox is that it adheres strictly to the APIs specified by the [PyTorch](https://pytorch.org/) machine learning framework. For example, the rAI-toolbox frames the process of solving for an adversarial perturbation solely in terms of the `torch.nn.Optimizer` and `torch.nn.Module APIs`. This makes it trivial to leverage other libraries and frameworks from the PyTorch ecosystem to bolster your responsible AI R&D. For instance, one can naturally leverage the rAI-toolbox together with [PyTorch Lightning](https://www.pytorchlightning.ai/) to perform distributed adversarial training.

- [rAI-toolbox Github](https://github.com/mit-ll-responsible-ai/responsible-ai-toolbox/)
- [rAI-toolbox documentation](https://mit-ll-responsible-ai.github.io/responsible-ai-toolbox)

```python
pip install rai-toolbox
```
