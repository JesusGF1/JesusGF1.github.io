Polygenic risk assessment is crucial in modern healthcare as it enables personalized medicine by estimating an individual's genetic predisposition to various conditions or phenotypes (including disease). This approach allows for early intervention, better resource allocation in healthcare systems, and improved risk stratification when combined with traditional risk factors. It's also important in biological research as it can discover new targets for drug development and protein design. Although important, polygenic risk scores are not deterministic, as environmental factors and lifestyle choices also influence disease development. One of the biggest caveats with polygenic scores is their limited portability between different groups of individuals (Genetic ancestry, Household income...) (1). This translates to reduced risk assesment accuracy in understudied populations, lowering the applicability of this techniques and augmenting health disparities in underrepresented groups. 
The classical way to calculate PGS portability involved population-level statistics (R^2) (2), these metrics although useful run into the problem of decreased PGS accuracy. The further each invididual gets from the "center" of the study population (aggregated results for all the individuals studied), the worse the risk assesment becomes. (3) . In the paper "Polygenic scoring accuracy varies across the genetic ancestry continuum", the authors propose to move towards metrics that take into account the continuum space of genetic backgrounds present in the population. This change should obtain more accurate, robust and unbiased results.





Genomics: A genomic featurization for an individual consists of polygenic risk scores (PRSs) for 7,415 traits. Each PRS estimates the genetic risk of the individual for a particular disease or trait, calculated by aggregating the estimated effects of many common variants associated with the condition. Each PRS was computed using genome-wide association study summary statistics computed by the PanUKB Consortium (Pan-UKB team, 2020). These genomic features were then converted to images by projecting the PRSs into patch-aligned squares of 8 × 8 pixels with values between [0, 255]. The 3 RGB channels of the images were used to stack 3 different p-value thresholds of the projections. The PRS features were obtained from the genetic information of 314,540 individuals of European genetically inferred ancestry from the UK Biobank (Bycroft et al., 2018; Sudlow et al., 2015).

To create training and evaluation labels, we selected eight in-distribution health outcomes which have strong heritability (i.e. genetic information plays an important role in influencing susceptibility (Visscher et al., 2008)), span multiple organ systems, and are challenging to predict from polygenic risk scores alone: coronary artery disease, stroke, type 2 diabetes, glaucoma, chronic obstructive pulmonary disease (COPD), rheumatoid arthritis, major depression, and all-cause mortality. Additionally, to assess model generalization, we selected six out-of-distribution (OOD) health outcomes that share genetic correlation with one or more of the in-distribution health outcomes: hypertension, hypercholesterolemia, atrial fibrillation, diabetic retinopathy, asthma, and pneumonia (Table A.10).

Transformer Decoder (Parmar et al., 2018; Vaswani et al., 2017), from foundational Google research on Flamingo (Alayrac et al., 2022), CoCa (Yan et al., 2022; Yu et al., 2022) and PaLI (Chen et al., 2022), enabling enhanced multimodal understanding and reasoning. Given this exceptional efficiency, we chose to finetune Med-Gemini from Gemini 1.5.

Personalized medicine can benefit greatly from genetics, as disease risks depend heavily on an individual’s genetic makeup. To leverage this powerful information, we expanded our model’s ability to process genetic information in the form of an RGB image by featurizing the genome into polygenic risk scores (PRS) as explained in Section 2. To assess the disease risk prediction capability of Med-Gemini-Polygenic, we created benchmarks by training linear models on all PRS featurizations plus demographics (“Ensemble of PRSs and demographics”) which is the current best practice for using PRSs for disease prediction (Albiñana et al., 2023; Truong et al., 2024). For in-distribution health outcomes (see Section 2) used in MedGemini-Polygenic training, we directly applied the trained “Ensemble of PRSs and demographics” models as benchmarks. For health outcomes that were never used in the training process (outof-distribution or OOD, see Section 2) but share some genetic correlation with the in-distribution outcomes, we first calculated their phenotypic correlations with all the in-distribution outcomes, and used the model trained to predict the most correlated in-distribution outcome to generate a maximally strong performance benchmark. We evaluated Med-Gemini-Polygenic performance on case/control balanced datasets sampled from the test split (200 cases, 200 controls per outcome) for computational efficiency (Section A.2.2). We obtained a disease probability score from Med-Gemini-Polygenic by prompting it to predict the status of a given health outcome using a text prompt and the genetic risk “image” (Table A.9), and computed the probability as the ratio of the likelihoods of the model generating a positive and negative prediction. Med-Gemini-Polygenic achieved higher AUCs than the PRS linear model benchmarks for all in-distribution health outcomes except glaucoma (Figure 5). To evaluate zero-shot generalization ability, we prompted Med-Gemini-Polygenic to predict disease status for the six out-of-distribution health outcomes. Med-Gemini-Polygenic achieved similar performance to benchmarks trained on the most correlated in-distribution outcome (Table A.11) despite never being instructed about the associations between in-distribution and out-of-distribution outcomes (Figure 5). Additionally, we compared the performance of linear probes of the Med-Gemini-Polygenic embeddings and directly prompting Med-Gemini-Polygenic in the evaluation sets of 400 individuals. Comparisons of the AUCs show that while Med-Gemini-Polygenic performs similarly to the linear probe when each is only given demographic information, it often outperforms the linear probe when incorporating both PRSs and demographics (Figure A.5). This performance increase is largely attributable to Med-Gemini-Polygenic modeling non-linear interactions between genomic information and demographics (Table A.12). We caution that the AUC values reported here represent an upper bound on model performance since the GWASs used to create the PRS features were performed within the UK Biobank. However, the relative performance of different models that all operate on this in-sample data is the measure of interest for these analyses.


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
Gemini: 
Gemini 1.5:
Mixture of Experts: 
Context window: 
Routing:
Contrastive learning:


Functions described: 

Correlation of an individual's genetic liability and PGS estimate:
r_i^2(g_i, \hat{g}_i) = \frac{\text{cov}_{\beta,D}(g_i,\hat{g}_i)^2}{\text{var}_\beta(g_i)\text{var}_{\beta,D}(\hat{g}_i)} = 1 - \frac{E_D(\text{var}_{\beta|D}(x_i^\top\beta))}{\text{var}_\beta(x_i^\top\beta)}

Under infinitesimal assumption for which all variants are causal and drawn from a normal distribution:

r_i^2(g_i, \hat{g}_i) = 1 - \frac{\sigma_\varepsilon^2 \sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{\sigma_\beta^2 x_i^\top x_i} = 1 - \frac{\sigma_\varepsilon^2}{\sigma_\beta^2} \frac{\sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{x_i^\top x_i}

In which σ 2β is per single nucleotide polymorphism (SNP) heritability; σe2 is the variance of residual environmental noise; vj and λj are the jth eigenvector and eigenvalues of training genotype data and J is the total number of eigenvectors. xvvx ∑j J λ i j ji =1 1 j ⊤⊤is the squared Mahalanobis distance of the testing individual i from the centre of the training genotype data on its principal component (PC) space; and x x ii ⊤ is the sum of squared genotypes across all variants
The metric here is an upper bound of genetic prediction accuracy

References:
1 - Martin, A. R. et al. Clinical use of current polygenic risk scores may exacerbate health disparities. Nat. Genet. 51, 584–591 (2019).
2 - Lambert, S. A., Abraham, G. & Inouye, M. Towards clinical utility of polygenic risk scores. Hum. Mol. Genet. 28, R133–R142 (2019).
3 - Polygenic scoring accuracy varies across the genetic ancestry continuum
- Advancing Multimodal Medical Capabilities of Gemini

-
-
-
-
