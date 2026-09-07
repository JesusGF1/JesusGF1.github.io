---
layout: post
title: "What would a virtual brain organoid actually be?"
date: 2026-09-07
tags: [Neuroscience, Deep Learning]
published: false  # held until the VBO review is submitted
excerpt: "Brain organoids have gotten surprisingly good. What the field still does not have is a shared predictive model: something you could give a genotype and a perturbation, and ask what the tissue is going to do next."
---

Brain organoids have gotten surprisingly good. Protocols are more reproducible, cultures can be maintained for months or even years, and the amount of data we can collect from them keeps growing. We can perturb organoids at scale and measure transcriptomics, chromatin accessibility, imaging, and electrical activity, sometimes from the same tissue.

What the field still does not have is a shared predictive model. Something you could give a genotype and a perturbation, and ask: what is this tissue going to do next?

Without that, most organoid work is still descriptive. We can characterize differences in cell types, gene expression, morphology, or activity, but predicting how the system will respond to a new perturbation is much harder.

The natural next step is something like a tissue-scale version of the virtual cell. A **virtual brain organoid**.

## Why would we want one?

The main reason is that organoids are becoming too complex and too expensive to study entirely by trial and error.

A single experiment can involve months of culture, many cell lines, repeated recordings, and destructive molecular assays. Even if we could measure everything we wanted, we could never experimentally test every combination of genotype, developmental stage, drug, stimulation pattern, and environmental condition.

A useful virtual organoid would let us explore some of that space computationally before going back to the dish.

That could mean predicting which perturbations are most likely to rescue a disease-associated phenotype, identifying when during development an intervention is most likely to work, or estimating how a genetic variant will alter the trajectory of a circuit rather than just its endpoint.

It could also help connect measurements that are currently studied separately. A transcriptional change is interesting, and a change in network activity is interesting, but the harder question is how one leads to the other. A model that tracks the state of the same tissue across molecular, cellular, and circuit scales could start to make those relationships testable.

There is also a practical reason. Organoid experiments are slow. If a model can rule out uninformative experiments, prioritize perturbations, or tell us what measurement would be most useful next, it becomes part of the experimental process itself. The point would not be to replace the organoid. It would be to make each experiment more informative.

And eventually, the most interesting use may be the simplest one: asking questions that are difficult to answer experimentally. What happens if this mutation occurs in this cell type, at this developmental stage, under this pattern of activity? What would have happened to this same organoid under a different perturbation? Those are counterfactual questions, and biology is not very good at giving us counterfactuals.

A virtual organoid could be.

## Why it might actually be possible

A few things have come together recently.

* **The biology is stable enough to follow over time.** Organoids can now be cultured for months or years while maintaining meaningful developmental changes. That makes longitudinal modeling much more realistic than it used to be.
* **We can measure much more of the system.** Single-cell genomics, high-density MEAs, spatial transcriptomics, and volumetric imaging give us different views of the same tissue. Perturbation screens also provide exactly the kind of perturbation and outcome pairs needed to train predictive models.
* **We are getting better at compressing complex biology.** Representation learning and dynamical models can reduce high-dimensional population activity into a smaller state space where trajectories become easier to compare and predict.
* **Biophysical models are becoming easier to fit to data.** Instead of choosing parameters by hand from the literature, differentiable simulators make it possible to optimize parts of a mechanistic model directly against experimental recordings. That creates a much more interesting middle ground between purely data-driven prediction and biological mechanism.

## Why it is not here yet

There are still some very real problems.

* **We only observe part of the system.** Even dense MEAs record a small fraction of the neurons in an organoid. Two neurons that appear tightly coupled might not be connected at all. They could simply be responding to the same unobserved input. The same problem appears in biophysical models, where many different parameter combinations can produce almost identical dynamics.
* **Important biology is still missing.** Many organoid systems lack mature vasculature, immune components such as microglia, or other features of the in vivo environment. A model trained only on those systems will probably fail when a perturbation depends on something that is not represented.
* **Batch effects can be enormous.** Differences between labs, cell lines, differentiation protocols, and recording systems can be as large as, or larger than, the biological effects we actually want to predict. A useful virtual organoid would have to generalize across at least some of that variation.
* **There is no obvious endpoint.** Long-term cultures generate enormous amounts of data while the tissue is continuously changing. Summarizing that history without throwing away the maturation process is not a trivial problem.
* **We do not have shared benchmarks.** Right now, there is no agreed way to evaluate whether a model can really predict organoid dynamics. Different labs use different datasets, perturbations, recording modalities, and metrics, which makes it very difficult to compare models.

## So where does that leave us?

I do not think a true virtual brain organoid exists yet, but I think it is plausible within the next five to ten years.

What makes me optimistic is that most of the individual pieces are already moving quickly. We have better organoids, richer measurements, large perturbation datasets, stronger representation learning methods, and increasingly useful mechanistic simulators.

The harder problem is putting those pieces together in a way that works across labs, cell lines, and experimental systems.

That may be less of an algorithm problem than a coordination problem.

The Virtual Cell Challenge gave the single-cell field a shared prediction task and a common way to evaluate progress. There is nothing comparable yet at the tissue or circuit level. Until there is, a statement like "our model predicts organoid dynamics" is difficult to interpret because there is no common test for what that should mean.

That is the part I am most interested in helping build. Not only models that make predictions, but the datasets and benchmarks that let us find out whether those predictions actually hold up.

---

*Drawn from a review I have been writing with Luiz F. S. Eugenio dos Santos, Avelina Moreno-Ochando, and Mohammed A. Mostajo-Radji.*
