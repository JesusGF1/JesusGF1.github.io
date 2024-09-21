Polygenic scoring accuracy varies across the genetic ancestry continuum






Advancing Multimodal Medical Capabilities of Gemini

Genomics: A genomic featurization for an individual consists of polygenic risk scores (PRSs) for 7,415 traits. Each PRS estimates the genetic risk of the individual for a particular disease or trait, calculated by aggregating the estimated effects of many common variants associated with the condition. Each PRS was computed using genome-wide association study summary statistics computed by the PanUKB Consortium (Pan-UKB team, 2020). These genomic features were then converted to images by projecting the PRSs into patch-aligned squares of 8 × 8 pixels with values between [0, 255]. The 3 RGB channels of the images were used to stack 3 different p-value thresholds of the projections. The PRS features were obtained from the genetic information of 314,540 individuals of European genetically inferred ancestry from the UK Biobank (Bycroft et al., 2018; Sudlow et al., 2015).

To create training and evaluation labels, we selected eight in-distribution health outcomes which have strong heritability (i.e. genetic information plays an important role in influencing susceptibility (Visscher et al., 2008)), span multiple organ systems, and are challenging to predict from polygenic risk scores alone: coronary artery disease, stroke, type 2 diabetes, glaucoma, chronic obstructive pulmonary disease (COPD), rheumatoid arthritis, major depression, and all-cause mortality. Additionally, to assess model generalization, we selected six out-of-distribution (OOD) health outcomes that share genetic correlation with one or more of the in-distribution health outcomes: hypertension, hypercholesterolemia, atrial fibrillation, diabetic retinopathy, asthma, and pneumonia (Table A.10).

Transformer Decoder (Parmar et al., 2018; Vaswani et al., 2017), from foundational Google research on Flamingo (Alayrac et al., 2022), CoCa (Yan et al., 2022; Yu et al., 2022) and PaLI (Chen et al., 2022), enabling enhanced multimodal understanding and reasoning. Given this exceptional efficiency, we chose to finetune Med-Gemini from Gemini 1.5.


Glossary:

Polygenic score: Estimates of an individual’s genetic predisposition for complex traits and diseases (that is, genetic liability; also referred to as genetic value).
Polygenic risk score:
R2 test:
Biobank:
Genetic distance (In paper): GD is defined as a PCA projection of the target individual on the training data used to estimate the PGS weights
Pearson correlation:
Genetically inferred ancestry (GIA): Describes the genetic similarity of an individual to a reference dataset (for example, 1000 Genomes) as inferred by methods such as principal component analysis (PCA).
Heritability:
Population (In genetics terms):
Mixed models: 
Relatedness:
Ancestry groupings: 
Admixture: 
Mahalanobis distance: 
Upper bound metric: 
LDpred2: 
Genetic background:
Credible interval:
GWAS Genome Wide association study: 




Functions described: 

Correlation of an individual's genetic liability and PGS estimate:
r_i^2(g_i, \hat{g}_i) = \frac{\text{cov}_{\beta,D}(g_i,\hat{g}_i)^2}{\text{var}_\beta(g_i)\text{var}_{\beta,D}(\hat{g}_i)} = 1 - \frac{E_D(\text{var}_{\beta|D}(x_i^\top\beta))}{\text{var}_\beta(x_i^\top\beta)}

Under infinitesimal assumption for which all variants are causal and drawn from a normal distribution:

r_i^2(g_i, \hat{g}_i) = 1 - \frac{\sigma_\varepsilon^2 \sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{\sigma_\beta^2 x_i^\top x_i} = 1 - \frac{\sigma_\varepsilon^2}{\sigma_\beta^2} \frac{\sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{x_i^\top x_i}

In which σ 2β is per single nucleotide polymorphism (SNP) heritability; σe2 is the variance of residual environmental noise; vj and λj are the jth eigenvector and eigenvalues of training genotype data and J is the total number of eigenvectors. xvvx ∑j J λ i j ji =1 1 j ⊤⊤is the squared Mahalanobis distance of the testing individual i from the centre of the training genotype data on its principal component (PC) space; and x x ii ⊤ is the sum of squared genotypes across all variants
The metric here is an upper bound of genetic prediction accuracy

References:
-
-
-
-
