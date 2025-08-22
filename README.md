# PholdAPhage

<p align="center">
<img width=25% height=auto alt="image" src="https://github.com/user-attachments/assets/a6b22538-5c11-4f08-bdb4-76c6f9c055fd" />
</p>


Assemble unknown phage particles one protein at a time.

**_PholdAPhage_** is a predictive modelling tool for the quick, efficient visualisation of unknown phage structures for experimental baseline. Traditional wet lab experiments to define protein morphology are time consuming and expensive. PholdAPhage supports the three dimensional reconstruction of unknown phage structures, utilising AlphaFold2, oligomeric state prediction, and predictive simulation by ChimeraX. 
<br><br>

<h2>Background</h2>

**What is a phage?**

Bacteriophages (phages) are viruses which infect bacteria and are the most abundant and diverse biological agents on earth. They consist of three main components: a capsid protein head, a nucleic acid genome, and tail for bacterial interaction. Presenting therapeutic opportunities as viral vectors and antimicrobials, many of their structures are unknown, with head and tail composition different for each phage. Structural differences which pose challenges in understanding their molecular composition and application for phage therapy. PholdAPhage provides a novel approach to structurally modelling unknown novel phages for baseline and visualisation.

**How does PholdAPhage work?**

Phage capsid structures are highly conserved, 96% are icosahedral in nature applying mathematical principles of symmetry to shape their protein capsids proportional to genome length. PholdAPhage exploits this evolutionary capsid design principle, employing symmetry type and genome length, to predict an unknown phages triangulation number (or T-number), for protein copy number in support of computational simulation. 
<br><br>

<p align="center"><strong>Icosahedral lattice symmetry types</strong></p>
<p align="center">
<img width=60% height=auto alt="image" src="https://github.com/user-attachments/assets/7fa14d17-31ab-4bb2-a8e7-650c98bc8568" />
</p>
<p align="center">
  Figure 1: Example of differing icosahedral lattices employing the theory of viral symmetry for T=7 phage capsids in support of increased capsid size. 
</p>
<br><br>

<p align="center"><strong>Casper-Klug formula</strong></p>

<p align="center">
<img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/d44052c3-4f68-4772-ae4d-bf2271f38251" />
</p>
<p align="center">
  Figure 2: Casper-Klug formula for viral symmetry to determine T-number and capsid protein number. The Theory is built on 60 identical subunits organized on the 20 triangles creating the faces of the icosahedral shape.
</p>
<br><br>
Example: A phage genome length of ~5,000bps, by research indicates a phage capsid T# of 1. A T#=1 capsid incorporates 60 major capsid proteins simulated across the capsid structure. hkcage parameters would be  _(h, k)_ as (1, 0) for T#(1,0) =_1_^2 + _1x0_ +_0_^2 = 1. More information at [viral zone](https://viralzone.expasy.org/8577).
<br><br>

<h2>Brief overview</h2>

**Novel method**
<!--<br><br>
<img width=100% height=auto alt="image" src="https://github.com/user-attachments/assets/391993b5-6674-49e5-891c-766dc3367faa" />
<br><br>-->
<img width=100% height=auto alt="image" src="https://github.com/user-attachments/assets/73cbb970-c9e8-4f32-a47d-26bcb74b4c97" />
<br><br>

Genome length is proportional to capsid size for DNA packaging. 

Using the Casper-Klug (CK) Theory of viral symmetry:
- Step 1: defines your phage's capsid triangulation number (T#) by the Genome-to-T-number model
- Step 2: takes your T#, and it's _(h, k)_ parameters to simulate the correct protein copy number across a phage capsid structure in ChimeraX. 
<br><br>

<h2>How to simulate your unknown phage</h2>

**<mark>Pre-simulation needs</mark>**
- You will need to know you phage genome length
- You will need your phage genome annotated and folded for use. To do this visit Pharokka, Phyntenny and AlphaFold2
- have downloaded or have access to ChimeraX for protein visualisation
<br><br>

**<mark>STEP 1 - Define your unknown phage T# and protein copy number</mark>**

1. Define T-number (T#)

   Use your genome length (in bps) to determine your T#. If you know your phage capsid diameter, this can also help. To determine your phages T# you can start with the following links:

   - [The Missing Tailed Phages: Prediction of Small Capsid Candidates](https://pmc.ncbi.nlm.nih.gov/articles/PMC7762592/)
   - link 2
   - link 3

2. Define protein copy number

   The rules of geometric icosahedral symmetry indicate an increase of 1 for T#, would see an increase of 60 asymmetric units. Following this rule, a T=1 will have 60 asymmetric units, a T=2 would have 120, and a T=13 would have 780 asymmetric units.

   Use your defined T# to determine how many assymetric units you have.

3. Define your T# parameters for use in simulation.

   The Casper-Klug formula uses h, k parameters to define the T# based on symmetry. Therefore, knowing your T# you can work backwards to determine what these will be using the formula.


   For example for a T# of 1 your (h, k) values would be  (1, 0) in support of the following 1 =_1_^2 + _1x0_ +_0_^2. In this sense you can work to find yours. Here are a few examples: 

   - T#7 or (2 ,1) = _2_^2 + _2x1_ +_1_^2
   - T#9 or (3 ,0) = _3_^2 + _3x0_ +_0_^2
   - T#13 or (3 ,1) = _3_^2 + _3x1_ +_1_^2


   Following this same train of though, use your T# to determine your formula parameters.
<br><br>

**<mark>STEP 2 - Simulate your phage structure in ChimeraX</mark>**

1. Download the attached _script.cxc_ to your desktop
2. Open _script.cxc_ in terminal and update/save your parameters
5. Run script through:
   -  terminal by typing --script ~/Desktop/script.cxc
   -  ChimeraX by command line runscript _script.cxc_

To include more proteins in the simulation.

With the simulation still open:
1. type _open name.pdb_ in the command line (where _open name_ is the name of your file)
2. Move and place the new protein on your hkcage where you require it using ChimeraX _right mouse tools_
3. Run another _Sym_ command by typing _sym #x #y i,222_ where:
   - x = the protein models ID,
   - y = the hkcage models ID,
   - _i_ indicates the symmetry type (i being icosahedral),
   - and _222_ syms it as two-fold symmetry on the X, Y, and Z axis.
   For more options go see [ChimeraX Sym command page](https://www.cgl.ucsf.edu/chimerax/docs/user/commands/sym.html).
<br><br>


<h2>Version log</h2>
PholdAPhage is a novel method to unknown phage development in 2025. Current release V1.
<br><br>

<h2>Bugs and Suggestions</h2>
If you come across bugs with PholdAPhage, or would like to make any suggestions to improve the method, please open an issue or email renee.green@flinders.edu.au  
<br><br>

<h2>Acknowledgements</h2>
Molecular graphics images were produced using the UCSF Chimera package from the Computer Graphics Laboratory, University of California, San Francisco (supported by NIH P41 RR-01081). Annotation analysis and protein folding to support development of this methods completed using Pawsey Supercomputing Research Centre (Perth, Australia) which is funded by the Australian Government. 
<br><br>

<h2>How to cite</h2>

If you use **PholdAPhage**, I would recommend a citation in your manuscript along the lines of:

All predictive modelling of phages were done using the PholdAPhage modelling protocol (Green et al. 2023). Specifically, genome annotations completed with Pharokka v ___ (Bouras, et al. 2023), and Phynteny (Grigson, et al 2025). Folds completed with AlphaFold2, with ogliomeric predictions completed with XXXXXX (Grigson, et al 2025). Predictive modelling and simulation completed by UCSF ChimeraX package and sym command by the Computer Graphics Laboratory, University of California, San Francisco, and UCSF ChimeraX package hkcage command by Luque Lab at San Diego State University. with funding from the NSF.

With the following full citations for the constituent tools below where relevant:

- George Bouras, Roshan Nepal, Ghais Houtak, Alkis James Psaltis, Peter-John Wormald, Sarah Vreugde, Pharokka: a fast scalable bacteriophage annotation tool, Bioinformatics, Volume 39, Issue 1, January 2023, btac776, https://doi.org/10.1093/bioinformatics/btac776
- Grigson, S.R., Bouras, G., Papudeshi, B., Mallawaarachchi, V., Roach, M.J., Decewicz, P., & Edwards, R.A. (2025). Synteny-aware functional annotation of bacteriophage genomes with Phynteny. bioRxiv, 2025.07.28.667340. https://doi.org/10.1101/2025.07.28.667340.
- Grigson, S.R. ...
- Jumper, J. et al. “Highly accurate protein structure prediction with AlphaFold.” Nature, 596, pages 583–589 (2021). DOI: 10.1038/s41586-021-03819-2
- Pettersen, E.F., Goddard, T.D., Huang, C.C., Couch, G.S., Greenblatt, D.M., Meng, E.C., and Ferrin, T.E. "UCSF Chimera - A Visualization System for Exploratory Research and Analysis." J. Comput. Chem. 25:1605-1612 (2004). http://www.cgl.ucsf.edu/chimera
- Mirdita, M. et al. “ColabFold: Making protein folding accessible to all.” Nature Methods, 19, pages 679–682 (2022). DOI: 10.1038/s41592-022-01488-1



