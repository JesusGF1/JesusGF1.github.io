

[Many datasets from the Allen Institute](https://portal.brain-map.org/cell-types/classes/multimodal-characterization)


# PAPER 1: Integrated Morphoelectric and Transcriptomic Classification of Cortical GABAergic Cells MOUSE
Number of cells profiled: 4,200 standardized, quality-controlled (QC) Patch-seq recordings from GABAergic interneurons in visual cortex of the adult mouse.
The dataset, freely available to the public via https:// portal.brain-map.org.
For a subset (517 cells) of transcriptomically and electrophysiologically characterized neurons from the Sst, Pvalb, Vip, Sncg, and Lamp5 subclasses morphological analyses was also performed. Morphologies from selected t-types are aligned to an average cortical template, followed by soma depth distributions and averaged dendrite and axon depth distributions.


GABAergic cortical interneurons of the mouse visual cortex can be defined into 28 types based on their morphological, electrophysiological, and transcriptomic properties and are distinguished by their layer-specific axon innervation patterns.

Transcriptomic and electrophysiology subtypes are not always 1 to 1. 

### Summary of Electrophysiological Analysis

Electrophysiological features were measured from neuronal responses to short (3 ms) and long (1 s) current pulses. Action potentials (APs) were detected using the derivative of membrane potential (dV/dt) and refined based on voltage thresholds, peak height, and timing. Key AP characteristics—threshold, peak, fast trough, width at half-height, and upstroke/downstroke ratio—were calculated.

Waveforms from initial APs were concatenated for sparse principal component analysis (PCA), including derivatives. Inter-spike interval (ISI) trajectories were analyzed by normalizing durations and averaging traces. AP features were compared across long current steps using 20 ms binning and interpolation where necessary.

Instantaneous firing frequency and its adaptation were analyzed relative to maximum firing rates. Subthreshold responses to hyperpolarizing steps were examined, including membrane potential changes before and after stimulus. Responses were downsampled and normalized for consistency.

Datasets were built by accumulating feature vectors (AP waveforms, long-step AP features, subthreshold responses, etc.). Sparse PCA was performed on each dataset, retaining components explaining >1% variance. A total of 44 components were identified, z-scored, and used to create a reduced-dimension feature matrix. The data was then visualized using a two-dimensional projection via Uniform Manifold Approximation.


### Sequencing Technology  
- **SMART-Seq v4** was used for cDNA synthesis and sequencing.  
- This method was consistent with the transcriptomic study by *Tasic et al., 2018*.  

### RNA Isolation  
- Both **nuclear and cytosolic mRNA** were extracted from patched cells.  
- RNA was reverse transcribed before sequencing.  

### Electrophysiological Characterization  
- Whole-cell patch-clamp recordings captured neuronal responses.  
- Cells were stimulated with **hyperpolarizing and depolarizing current injections**.  
- Soma locations and cortical depths were mapped using the **Allen Mouse Common Coordinate Framework (CCF)**.  

## Major Subclasses of Cortical GABAergic Neurons in Mouse:

1. **Parvalbumin (Pvalb)-positive cells**  
   - Basket cells (and related cells)  
   - Chandelier cells  

2. **Somatostatin (Sst)-positive cells**  
   - Martinotti cells  
   - Non-Martinotti cells  

3. **Vasoactive Intestinal Peptide (Vip)-positive cells**  
   - Bipolar cells  
   - Bitufted cells  
   - Multipolar cells  

4. **Lamp5 (formerly Htr3a+/Vip–) cells**  
   - Neurogliaform cells  
   - Single bouquet cells  

5. **Sncg-positive cells** (related to Vip and Lamp5 subclasses)  


## Correlation of Transcriptomic Types (t-types) to Morphoelectric Types (metypes)

The relationship between transcriptomic and electrophysiological properties raises the question of whether neuronal electrophysiology can be quantitatively predicted from single-cell RNA sequencing (scRNA-seq) data. Several challenges exist, including technical noise in gene expression measurements and discrepancies between transcript and protein levels. However, initial tests using sparse regression models suggest that ion channel gene expression can predict certain electrophysiological features, with varying accuracy across different components.

### SST Morphoelectric Types (met-types)
| Transcriptomic Type (t-type)       | Morphoelectric Type (metype)                                   |
|------------------------------------|---------------------------------------------------------------|
| **Sst Chodl**                     | Nos1+ long-projecting Sst neurons                           |
| **Sst-MET-1**                     | Non-Martinotti, long-range projecting inhibitory neurons    |
| **Sst-MET-2 (Sst Tac1 Htr1d)**     | Exhibits electrophysiological properties similar to Pvalb interneurons |
| **Sst-MET-3 (Sst Calb2 Pdlim5, L2/3)** | L2/3 Martinotti cells                                      |
| **Sst-MET-4 (Sst Calb2 Pdlim5, L5)** | L5/6 fanning-out Martinotti cells                          |
| **Sst-MET-5 (Sst Nr2f2 Necab1)**   | L5 neurons with burst-like or strongly adapting firing patterns |
| **Sst-MET-6 (Sst Myh8 Etv1, Sst Chrna2 Glra3)** | T-shaped and alpha-2 Martinotti cells                     |
| **Sst-MET-7 (Sst Hpse Sema3c)**    | T-shaped Martinotti-like cells                             |
| **Sst-MET-8 (Sst Hpse Cbln4)**     | L5 non-Martinotti cells in somatosensory cortex           |
| **Sst-MET-9 (Sst Tac2 Tacstd2)**   | L5 neurons primarily innervating that layer with some projection to L1 |
| **Sst-MET-10 (Sst Rxfp Prdm8)**    | L5 neurons with deep-layer innervation and sparse L2/3/L4 projections |
| **Sst-MET-11**                     | L5 neurons with low upstroke/downstroke ratio and low input resistance |
| **Sst-MET-12 (Sst Crhr2 Efemp1, Sst Rxfp1 Eya1, Sst Crh 4930553C11Rik)** | L5/L6 neurons primarily innervating deeper layers with few L1 projections |
| **Sst-MET-13 (Sst Esm1 Nts)**      | L5/L6 neurons with dominantly deep-layer axon innervation |

### Pvalb met-types

| Morphoelectric Type (metype)       | Transcriptomic Type (t-type)  | Description |
|------------------------------------|------------------------------|-------------|
| **Pvalb-MET-1**                   | Pvalb Gabrg1                 | L5/L6 basket-like cells with deep-layer axon and dendrites; exhibited more hyperpolarization-induced sag; expressed Gabrg1, Bche, and Th. |
| **Pvalb-MET-2**                   | Multiple Pvalb t-types       | L6 fast-spiking, locally projecting cells; deep basket cells; expressed Sema3e. |
| **Pvalb-MET-3**                   | Pvalb Reln Tac1              | L5 fast-spiking cells with L5-dominant axonal projection and some superficial layer collaterals. |
| **Pvalb-MET-4**                   | Pvalb Reln Itm2a, Pvalb Tpbg | L4 and L2/3 fast-spiking cells; dominant L2/3 axonal projection with sparse deeper-layer projections; translaminar connectivity. |
| **Pvalb-MET-5**                   | Pvalb Vipr2                  | Chandelier cells; higher input resistance compared to Pvalb-MET-4. |

### Lamp-5 met-types

### LAMP5 Morphoelectric Types (met-types)

Most Lamp5 cells fell into Lamp5-MET-1, while Lamp5 Lhx6 cells formed the distinct Lamp5-MET-2 type. Other potential met-types may exist among Lamp5 Krt73, Lamp5 Fam19a1 Pax6, and Lamp5 Fam19a1 Tmem182 cells, but these were not well-characterized due to limited data.

| Morphoelectric Type (metype)       | Transcriptomic Type (t-type)                | Description |
|------------------------------------|--------------------------------------------|-------------|
| **Lamp5-MET-1**                   | Lamp5 Lsp1, Lamp5 Plch2 Dock5, Lamp5 Ntn1 Npy2r | Neurogliaform-like morphology; found in L1, L2/3, and deeper layers; high upstroke/downstroke ratios; variation in morphology, gene expression, and electrophysiology; spectrum from low Npy expression with wide axons to high Npy expression with round axons and late-spiking phenotype. |
| **Lamp5-MET-2**                   | Lamp5 Lhx6                                 | Found in deep layers; similar electrophysiological properties to Lamp5-MET-1, with high upstroke/downstroke ratios and late-spiking; distinguishable by presence/absence of specific marker genes. |

### Sncg Morphoelectric Types (met-types)
Sncg-MET-1 was the most abundant met-type, whereas Sncg-MET-2 and Sncg-MET-3 contained very few characterized cells but had distinct properties.

| Morphoelectric Type (metype)       | Transcriptomic Type (t-type) | Description |
|------------------------------------|-----------------------------|-------------|
| **Sncg-MET-1**                    | Sncg (multiple t-types)     | Found in most cortical layers; bitufted or multipolar dendrites; wide, translaminar axon mostly avoiding L1; regular, adapting firing patterns; linked to Vip+/Cck+ basket cells. |
| **Sncg-MET-2**                    | Sncg (Car10, Nptx2)        | Few identified cells; found at L1-L2/3 border; very high input resistance. |
| **Sncg-MET-3**                    | Sncg Slc17a8               | Few identified cells; deep-layer location. |

# Paper 2: Human neocortical expansion involves glutamatergic neuron diversification (L1, L2 and L3)

Number of cells profiled: 
- A total of 385 neurons that passed transcriptomic data quality control mapped with higher confidence to the five supragranular human glutamatergic t-types than to any other neuron types.
- 283 passed electrophysiological analysis.
- 109 morphological
Same ephys processing as the previous dataset:
Electrophysiological features were measured from responses elicited by short (3 ms) current pulses and long (1 s) current steps as previously described9. In brief, action potentials were detected by first identifying locations where the smoothed derivative of the membrane potential (dV/dt) exceeded 20 mV ms−1, then refining on the basis of several criteria including threshold-to-peak voltage, time differences and absolute peak height.

### HUMAN Cortical Morphoelectric glutamatergic Types (met-types)
| **Cell Type**  | **Morphoelectric Properties** | **Related Cell Type**  | **Mouse VISP Relationship** | **Mouse ALM Relationship** |
|---------------|--------------------------------|------------------------|----------------------------|----------------------------|
| **LTK**      | Superficial, small apical dendrites, high input resistance, lower excitability | Homologous to mouse supragranular IT types | - | - |
| **GLP2R**    | Superficial, moderate dendritic complexity, electrophysiological properties similar to LTK | Homologous to mouse supragranular IT types | - | - |
| **FREM3** (Superficial) | Varies with cortical depth, long apical dendrites reaching L1, graded changes in morphoelectric properties | Homologous to mouse supragranular IT types | - | - |
| **FREM3** (Deep) | Larger basal dendrites, sparse apical dendrites in L1, increased sag and action potential upstroke/downstroke ratio | Similar to infragranular mouse IT types | **Adamts2** | **Lrg1** |
| **CARM1P1**  | Large cell bodies, extensive basal dendrites, sparse apical projections to L1, burst firing phenotype | Similar to infragranular mouse IT types, long-range projection neurons | **Agmat** | **Ptrf** |
| **COL22A1**  | Smaller, simple dendritic morphology, apical dendrites terminate before L1, high input resistance, increased excitability | Similar to human L5 IT neurons | **Rrad** | **Sla** |


# Paper 3: Signature morpho-electric, transcriptomic, and dendritic properties of human layer 5 neocortical pyramidal neurons
Number of cells profiled: 
n = 28 human n = 12 mouse with all of the modalities I am guessing

Step Current Injections:
Applied 1-second current steps from -150 pA to +50 pA in 20 pA increments.
Measured input resistance (RN), voltage sag, and rebound slope from voltage responses.
Chirp Stimulus:
Frequency increased linearly (1-15 Hz over 15 s) or logarithmically (0.2-40 Hz over 20 s).
Impedance amplitude (ZAP) was calculated using Fourier transform analysis.
Resonance frequency (fR) and resonance strength (Q) were derived from the impedance profile.
Impedance phase (ZPP) and total inductive phase (ZF) were also measured.
Depolarizing Current Steps:
1-second injections increasing by +50 pA/step.
Measured spike count, instantaneous firing rate, and gain (firing rate-current slope).
Single action potential properties such as threshold, width, fast afterhyperpolarization (AHP), spike frequency accommodation (SFA), and medium AHP (mAHP) were analyzed.
Dendritic plateau potentials were quantified by measuring area and width.

| Ephys Type | Transcriptomic Type (T Type) | Morphoelectric Characteristics | Electrophysiological Properties | Species Differences |
|------------|------------------------------|--------------------------------|--------------------------------|---------------------|
| **L5 ET (Extratelencephalic)** | Distinct from L5 IT (Intratelencephalic) | Large pyramidal somata, subcerebral axonal targeting, enriched for HCN1, GPCRs | Lower input resistance, pronounced voltage sag/rebound, higher resonance frequency, and 3 dB cutoff; enriched in HCN1, HTR1E (human-specific), HTR1F (shared) | More abundant in mice (20%-30% of L5 excitatory neurons) than in humans (2%-6%), macaques intermediate |
| **L5 IT (Intratelencephalic)** | Separate from L5 ET | Typically smaller pyramidal neurons, intracortical projections | Higher input resistance than ET neurons; IT-like 2 neurons show 2× higher input resistance and larger rebound potential than IT-like 1 | Present in all species but relatively more abundant in human L5 compared to L5 ET neurons |
| **L3 Pyramidal Neurons** | Not ET (Negative for FAM84B, POU3F1) | Large pyramidal neurons in humans/macaques, but distinct from L5 ET neurons | Unclear electrophysiological differences compared to L5 neurons | More prominent in primates but do not express L5 ET markers |
| **L5 ET-Specific Ion Channels** | Transcriptomically distinct expression pattern | Associated with subcerebral projections, neuromodulation sensitivity (e.g., BCL11B, GRIK1) | Enriched for HCN1, GPCRs; species-specific serotonin receptor expression: HTR1A/HTR1F (mouse), HTR1E/HTR1F (human) | Conserved in rodents and humans, but some genes show human-specific expression |
| **Physiologically Defined Subtypes (Human MTG)** | ET-like, IT-like 1, IT-like 2 | Strong correspondence between transcriptomic and physiological types | ET-like neurons have higher resonance, lower input resistance; IT-like 2 has highest input resistance and rebound potential | Clear distinctions maintained across species with some divergence |


# Paper 4: Phenotypic variation of transcriptomic cell types in mouse motor cortex
Number of cells profiled: 
We performed whole-cell recordings from more than 2,000 cells, of which 1,329 cells (from 266 mice).
Cells that showed poor mapping (owing to a low read count or excessive RNA contamination) were excluded, leaving 1,227 neurons for further analysis (817 inhibitory, 410 excitatory; 369 and 269 with morphological reconstructions, respectively). The resulting data set covered 77 out of the 90 neuronal t-types (Fig.  1a), with 73 t-types having at least one morphologically reconstructed neuron.

| t-Type                     | Morphoelectrical Properties                                    | Morphology                                      |
|----------------------------|--------------------------------------------------------------|------------------------------------------------|
| **Pvalb**                  | High firing rates                                           | Compact, dense axonal arborization            |
| **Pvalb Vipr2_2** (chandelier)  | Morpho-electrically homogeneous                          | Distinct axonal cartridges targeting AIS      |
| **Sst**                    | High hyperpolarization sag and rebound                      | Large, horizontally elongated dendrites       |
| **Sst Pvalb Calb2**        | High variability in max firing rate, some neurons classified as Pvalb | Intermediate between Sst and Pvalb            |
| **Vip**                    | Continuous variation in membrane time constant              | Bipolar or multipolar dendrites               |
| **Vip Mybpc1**             | Some neurons exhibit Sst-like firing                        | Branched axons, mixed orientation             |
| **Vip Mybpc1_2**           | High electrophysiological variability (input resistance, membrane time constant, rebound) | Varied axonal structures                      |
| **Vip Sncg**               | Low rebound, close to Vip Mybpc1_2 in t-SNE space           | Long, thin dendrites                          |
| **Lamp5**                  | Distinct electrophysiological properties                    | Sparse, widespread axons                      |
| **Lamp5 Egln3_1**          | Some neurons exhibit Vip- and Sst-like firing               | Hybrid morphology, some long-range axons      |
| **CT**                     | Mostly well separated from other families                   | Large, extensive apical dendrites             |
| **IT**                     | Overlaps with ET, continuous variation across layers        | Layer-dependent dendritic complexity          |
| **ET**                     | Overlaps with IT                                            | Deep-projecting, thick apical dendrites       |


# Paper 5: Patch-Seq Links Single-Cell Transcriptomes to Human Islet Dysfunction in Diabetes

Not neurons but many cells profiled: 1,369 cells profiled.

# Paper 6: Signature morphoelectric properties of diverse GABAergic interneurons in the human neocortex

Neurons profiled: 778 human neurons in cortical layers 2 to 6, across 44 out of 45 g-aminobutyric acid–producing (GABAergic) transcriptomic types.

| **Cell Type**        | **Transcriptomic Type**   | **Electrophysiological Properties**                                        | **Morphological Description**                                                                                         |
|----------------------|---------------------------|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| **PVALB WFDC2**       | PVALB                     | Significant electrophysiological differences between acute and culture paradigms, with differences in AP width and sag. 43/84 features differed across paradigms. Species differences were observed, with the acute mouse data showing variations in AP width when compared with the human data. | Consistent morphometric features between acute and culture paradigms. Cortical depth–matched neurons show similar UMAP clustering. |
| **SST**               | SST                       | Differences in electrophysiological responses between subclasses in UMAP, but detailed responses not specified.         | Morphological diversity, specific features not detailed.                                                                 |
| **VIP**               | VIP                       | Distinct electrophysiological features observed when comparing across subclasses in UMAP.                                 | Small cell bodies and bipolar dendrites, primarily found in L2 and L3. Enriched for VIP neuron types, with varied morphologies. |
| **LAMP5/PAX6**        | LAMP5/PAX6                | Electrophysiological features were separated in UMAP based on subclass distinctions.                                     | Neurogliaform morphologies, with stellate dendrites, numerous primary dendrites, and extensive axon branching. Shortest soma–to–branch tip distances. |
| **SST FRZB**          | SST FRZB                  | Electrophysiological features largely aligned with PVALB, including fast-spiking behavior, narrow APs, and consistent AP kinetics such as upstroke/downstroke ratio. Most features aligned with PVALB in acute and culture paradigms. | Morphologically more similar to PVALB basket cells than SST neurons, with features like horizontal axon extent and axon–dendrite dissimilarity. |
| **L4-5 SST STK32A**   | SST STK32A                | Quasi-fast-spiking electrophysiological behavior, preferentially targeting L4 pyramidal neurons in mice.               | Found predominantly in L4 and L5 with extensive axonal branching, particularly innervating L4 pyramidal neurons. |
| **SST CALB1**         | SST CALB1                 | Electrophysiological properties vary across morphological types. Sparse SST neurons show lower sag, higher adaptation ratio, and delayed AP firing compared to MCs and DBCs. | Four morphological types identified: MCs, DBCs, basket-like cells, and sparse SST. MCs have extensive L1 axons; DBCs have narrow axons with characteristic horse-tail morphology. |
| **Double Bouquet Cell (DBC)** | SST CALB1 / SST ADGRG6 | Higher sag ratio in all DBCs. Diverse firing patterns include accommodating, stuttering, and irregular spiking.           | Horse-tail morphology with ascending and descending narrow axon bundles, found in L2 (SST CALB1) and L3 (SST ADGRG6). Narrow, bitufted or multipolar dendrites. |
| **Pvalb 2 (Homologous to PVALB WFDC2)** | PVALB WFDC2 / Pvalb 2 | Species differences observed in AP width, sag, rheobase, and AP half-width between humans and mice. AP width differences were primarily driven by culture conditions. | Morphological features between species show differences in axonal and dendritic branching but no difference in total axon length. |
| **Sst 5 (Homologous to SST CALB1)** | SST CALB1 / Sst 5 | Clear electrophysiological separation between human and mouse data, with differences in AP firing rate and AP frequency-current curve slope. | Variations in morphological features between species, with mouse L2/3 Martinotti neurons compared to a more diverse set of L2/L3 human SST morphologies. |

