Polygenic scoring accuracy varies across the genetic ancestry continuum

Advancing Multimodal Medical Capabilities of Gemini





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

Functions described: 

Correlation of an individual's genetic liability and PGS estimate:
r_i^2(g_i, \hat{g}_i) = \frac{\text{cov}_{\beta,D}(g_i,\hat{g}_i)^2}{\text{var}_\beta(g_i)\text{var}_{\beta,D}(\hat{g}_i)} = 1 - \frac{E_D(\text{var}_{\beta|D}(x_i^\top\beta))}{\text{var}_\beta(x_i^\top\beta)}

Under infinitesimal assumption for which all variants are causal and drawn from a normal distribution:

r_i^2(g_i, \hat{g}_i) = 1 - \frac{\sigma_\varepsilon^2 \sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{\sigma_\beta^2 x_i^\top x_i} = 1 - \frac{\sigma_\varepsilon^2}{\sigma_\beta^2} \frac{\sum_{j=1}^J \frac{1}{\lambda_j} x_i^\top v_j v_j^\top x_i}{x_i^\top x_i}

In which σ 2β is per single nucleotide polymorphism (SNP) heritability; σe2 is the variance of residual environmental noise; vj and λj are the jth eigenvector and eigenvalues of training genotype data and J is the total number of eigenvectors. xvvx ∑j J λ i j ji =1 1 j ⊤⊤is the squared Mahalanobis distance of the testing individual i from the centre of the training genotype data on its principal component (PC) space; and x x ii ⊤ is the sum of squared genotypes across all variants
The metric here is an upper bound of genetic prediction accuracy
