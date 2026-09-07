---
layout: post
title: "What would a virtual brain organoid actually be?"
date: 2026-09-07
tags: [Neuroscience, Deep Learning]
published: false  # held until the VBO review is submitted
excerpt: "Brain organoids have gotten good. What the field still lacks is a shared predictive object — a model you can hand a genotype and a perturbation and get back what the tissue will do."
---

Brain organoids have gotten good. Protocols are reproducible across months, sometimes years. Recordings are dense. We can perturb organoids at scale and read out transcriptome, chromatin accessibility and spiking activity from the same tissue.

What the field does not have is a shared *predictive* object: a model you can hand a genotype and a perturbation, and get back what the tissue will actually do. Without one, organoid science stays structurally descriptive — rich in characterization, thin in prediction.

The obvious target is a tissue-scale analog of the virtual cell. Call it a **virtual brain organoid**.

## Why it might be close

Four things have converged more or less at once:

- **The biology holds still long enough.** Cultures now run for months to years with enough developmental fidelity to model longitudinally.
- **We can measure enough at once.** Single-cell genomics, high-density MEAs, spatial transcriptomics and volumetric imaging can populate a real state vector from the same sample — and pooled perturbation screens supply the (perturbation, outcome) pairs a predictor needs.
- **Representation learning compresses it.** Latent dynamical models turn population activity into geometry you can actually forecast in.
- **Simulators became differentiable.** Biophysical models can now be *fit* to recordings instead of hand-tuned from the literature, which puts mechanism and data-driven prediction in the same optimization loop.

## Why it isn't here yet

Being honest about this matters more than the optimism:

- **Subsampling and identifiability.** MEAs see a small fraction of neurons, so co-varying units may share an unrecorded driver rather than a synapse. And many different biophysical parameter sets produce identical dynamics — a gradient fit will happily hand you one without warning.
- **Missing pieces.** Most organoids have no microglia and no vasculature. A model trained on them will systematically mispredict exactly the perturbations that depend on those.
- **Batch effects may exceed the signal.** Cross-lab and cross-line variability can be larger than the perturbation effects you're trying to forecast. Whether that condition is met has not been shown.
- **No natural endpoint.** Month-long cultures generate terabytes with no terminal experiment, and nobody has solved how to summarize that without discarding the maturation signal.
- **No benchmarks.** There are no agreed metrics for circuit-level prediction in organoids, so every claim of predictive success is currently laboratory-specific.

## Where that leaves it

Not yet — but plausibly in five to ten years. The thing I keep coming back to is that the binding constraint isn't the modelling. Each of the four ingredients above is individually strong; what has never been demonstrated is their integration into something that transfers across labs and genotypes.

And the missing piece is a *coordination* problem, not an algorithmic one. The Virtual Cell Challenge gave single-cell prediction a common target to be scored against. There is no tissue-scale equivalent. Until there is, "our model predicts organoid dynamics" is a sentence that cannot be checked.

That's the part I'd most like to help build: not just the predictors, but the benchmarks that would let us find out whether they work.

---

*Drawn from a review I've been writing with Luiz F. S. Eugenio dos Santos, Avelina Moreno-Ochando and Mohammed A. Mostajo-Radji.*
