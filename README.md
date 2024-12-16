# Microscopy Hackathon: Team GANder

**Motivation:** The ferroelectric polarisation of thin film materials are strongly affected by both mechanical and electrostatic boundary conditions. As such, features in sample topography can often be correlated with particular ferroelectric domains. We wish to investigate if images of sample topography can be used to intuit sample ferroelectric polarisations.

**Problem definition:** We intend to access such correlations between topography and sample polarisation via Cycle-Consistent Adversarial Networks (CycleGANs), an image-to-image translation process that both determines the mapping from some dataset $A \to B$, as well as the inverse map for $B \to A$.

**Hackathon target:**
- Create a workflow that trains, tests and refines a CycleGAN to a particular sample.
- Determine correlations (if any) between sample topography and (piezoresponse force microscopy) amplitude and phase.
- Determine correlations between sample topography and other independent sample analysis.