# Microscopy Hackathon: Team GANder

_Ralph Bulanadi (University of Geneva, Switzerland)_

_Kieran Pang (Justus-Liebig-Universität Gießen, Germany)_

_Michelle Wang (Technical University of Denmark, Denmark)_

**Motivation:** The ferroelectric polarisation of thin film materials are strongly affected by both mechanical and electrostatic boundary conditions. As such, features in sample topography can often be correlated with particular ferroelectric domains. We wish to investigate if images of sample topography can be used to intuit sample ferroelectric polarisations.

**Problem definition:** We intend to access such correlations between topography and sample polarisation via Cycle-Consistent Adversarial Networks (CycleGANs), an image-to-image translation process that both determines the mapping from some dataset $A \to B$, as well as the inverse map for $B \to A$.

**Hackathon target:**
- Create a workflow that trains, tests and refines a CycleGAN to a particular sample.
- Determine correlations (if any) between sample topography and (piezoresponse force microscopy) amplitude and phase.
- Determine correlations between sample topography and other independent sample analysis.


**Background and Introduction:**

Ferroelectric materials spontaneously maintain an electric polarisation; ferroelastic materials spontaneously maintain an elastic strain. Many functional materials, such as lead titanate thin films (PbTiO</sub>3</sub>, PTO) simultaneously exhibit phases that are both ferroelectric and ferroelastic, and this combined ferroicity can be used extensively for transducer applications.

Ferroelectric polarisation can be readily observed at the nanoscale through piezoresponse force microscopy (PFM); a variant of atomic-force microscopy (AFM) in which a scanning probe is placed in contact with a sample, an oscillating voltage is applied through the sample, and the consequent (piezoelectric) mechanical oscillations are read. However, the application of a voltage into the sample can cause ferroelectric switching, charge injection, or other chemical changes into the system. Further, the tip being placed in contact with the sample could change or alter the sample surface. Methods that can determine ferroelectric polarisations with neither an external bias, nor tip–sample contact, could therefore be particularly useful for the study of ferroelectric materials.

We here therefore investigate ferroelastic-ferroelectric PTO thin films that contain both c-domains (with an out-of-plane polarisation and out-of-plane tetragonal distortions) and a-domains (with an in-plane polarisation, and similarly in-plane tetragonal distortions). As the domains have different polarisation axes, and strain axes, from one another, both domains appear distinct from each other in both AFM topography datasets, and PFM amplitude datasets. We have trained a generative adversarial network (GAN) [1] on both the Height and Amplitude channels of typical PFM measurements to attempt to encode such differences in a machine-learning model.


**Results:**

Training outputs of the GAN run on Height channels create falsified Amplitude channels that visually resemble the initial height channels. A particularly ideal example is shown in Fig. 1. Here, the Height Channel




**Conclusions and Outlook:**

We look at ferroelectric-ferroelastic multiferroicity; could we train a similar model to examine, eg. ferromagnetic-ferroelectric multiferroicity?

But it may be good to mention that gan synthesised images can then be used to supplement data for classification/regression models


**Methods:**

*Sample and Image Preparation:* PTO (140 nm)/SRO (20 nm)/STO (001) thin films were grown as previously detailed in Ref. [2]. In brief, five samples were grown simultaneously by pulsed laser deposition and bombarded with varying levels of He<sup>2+</sup> ions. Piezoresponse force microscopy was then performed in dual AC resonance tracking mode using _OPUS_ OSCM-Pt tips in an _Asylum Research_ Cypher with a 500 mV drive voltage. Images varied in scale from approximately 2 μm to 10 μm.

*Preliminary Data Processing:* `HeightRetrace` and `Amplitude2Retrace` channels were directly taken from the `.ibw` output files from the _Asylum Research_ software. These datasets were directly converted to grayscale `.jpg` files using the `gray` sequential colormap in the `matplotlib` Python package, and no further data processing, with the minimum height (amplitude) and maximum height (amplitude) set to black and white respectively. These `.jpg` files were then both rescaled to 256x256 pixels, and paired height and amplitude images were combined together to create a single 512x256 pixel image. These composited images were used for model training.

*Data Augmentation:*

*Model Training:* Our model was trained on 78 images for 40000 steps, which took approximately 3.5 hrs. The loss continued to decay over the entirety of the training model (Fig. 1).

**References:**

[1] Isola, Phillip, et al. "Image-to-image translation with conditional adversarial networks." Proceedings of the IEEE conference on computer vision and pattern recognition. 2017.

[2] Bulanadi, Ralph, et al. "Interplay between Point and Extended Defects and Their Effects on Jerky Domain-Wall Motion in Ferroelectric Thin Films." Physical Review Letters 133.10 (2024): 106801.
