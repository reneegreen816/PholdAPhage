<h1>PholdAPhage: Assemble unknown phage particles one protein at a time</h1>

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17216762.svg)](https://doi.org/10.5281/zenodo.17216762)

<p align="center"> 
  <img width=35% height=auto alt="image Phages being folded" src="https://github.com/user-attachments/assets/5eac2c23-ecb9-48d6-9bc2-ec433d377eea" />
</p>

**_PholdAPhage_** is a predictive modelling tool for the quick, efficient visualisation of unknown phage structures for experimental baseline. Traditional wet lab experiments to define protein morphology are time consuming and expensive. PholdAPhage supports the three dimensional reconstruction of unknown phage structures, utilising genome annotation, protein folding, and oligomeric state predictions, for predictive simulation by UCSF ChimeraX. 
<br><br>

<h2> Table of contents</h2>

- [Background](#background)
   - [What is a phage?](#what-is-a-phage) 
   - [How does PholdAPhage work?](#how-does-pholdaphage-work)
- [Method overview](#method-overview)
- [How to simulate your unknown phage](#how-to-simulate-your-unknown-phage)
   - [Pre-simulation needs](#pre-simulation-needs)
   - [Step 1 - Define your unknown phage T# and protein copy number](#step-1---define-your-unknown-phage-t-and-protein-copy-number)
   - [Step 2 - Simulate your phage structure in UCSF ChimeraX](#step-2---simulate-your-phage-structure-in-ucsf-chimerax)
   - [Further command considerations](#further-command-considerations)
- [Version Log](#version-log)
- [Bugs and suggestions](#bugs-and-suggestions)
- [Acknowledgements](#acknowledgements)
- [How to cite](#how-to-cite)
- [References](#references)
<br><br>

<h2>Background</h2>

<h3>What is a phage?</h3>

Bacteriophages (phages) are viruses which infect bacteria and are the most abundant and diverse biological agents on earth. They consist of three main components: a capsid protein head, a nucleic acid genome, and possible tail for bacterial interaction. Presenting therapeutic opportunities as viral vectors and antimicrobials, many of their structures are unknown, with head and tail composition different for each phage. Structural differences which pose challenges in understanding their molecular composition and application for phage therapy. PholdAPhage provides a novel approach to structurally modelling unknown novel phages for experimental baseline and visualisation.

<h3>How does PholdAPhage work?</h3>

Phage capsid structures are highly conserved, 96% are icosahedral in nature applying mathematical principles of symmetry to shape their protein capsids proportional to genome length. PholdAPhage exploits this evolutionary capsid design principle, employing symmetry type and genome length, to predict an unknown phages triangulation number (T-number or T#), for protein copy number in support of computational simulation. 
<br><br>

<p align="center"><strong>Icosahedral lattice symmetry types</strong></p>
<p align="center">
<img width=60% height=auto alt="image" src="https://github.com/user-attachments/assets/7fa14d17-31ab-4bb2-a8e7-650c98bc8568" />
</p>
<p align="center">
  Figure 1: Example of differing icosahedral lattices employing the theory of viral symmetry for T=7 phage capsids in support of increased capsid size (Luque et al., 2020).
</p>
<br><br>

<p align="center"><strong>Casper-Klug (CK) Theory</strong></p>

<p align="center"> 
  <img width=80% height=auto alt="image Casper-Klug formula" src="https://github.com/user-attachments/assets/3fce8eaa-7787-44c4-8c60-4c9758d3f2f4" />
</p>
<p align="center">
  Figure 2: Casper-Klug (CK) Theory and formula for viral symmetry to determine T# and capsid protein copy number. The theory is built on 60 identical subunits organized across 20 triangles which create the faces of the icosahedral shape (Comas-Garcia, 2024; SIB Swiss Institute of Bioinformatics - Viral Zone, 2025)
</p>
<br><br>
<p align="center"> 
  <img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/37a6e261-9376-4664-9297-3251189a4de7" />
</p>

<p align="center">
  Figure 3: T# defined by CK formula (h, k) parameters for capsid pentagon location for symmetry and lattice type. h and k being non negative integers used to define the number of units in a straight line from one pentagon to another, before shifting left or right to reach the next pentagon.  (Comas-Garcia, 2024; SIB Swiss Institute of Bioinformatics - Viral Zone, 2025)
</p>
<br><br>

Example: A phage genome length of ~5,000bps is typical to a phage capsid T# of 1. The CK formula being (h, k) or (1, 0) with T# (1, 0) = 1^2 + 1x0 + 0^2 = 1. This T#=1 capsid structure would see 60 major proteins or identical asymmetrical subunits (protein copy number) wrapped across the capsid structure. More information at [Viral Zone](https://viralzone.expasy.org/8577)
<br><br>

<h2>Method overview</h2>

<p align="center"> 
<img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/afa32bef-c882-4d93-8df1-3cbc00365483" />
</p>


Using the CK Theory of viral symmetry:
- Step 1: defines your phage's capsid T# by using the Genome-to-T-number model.
- Step 2: takes your defined T# and CK (h, k) parameters to simulate your protein copy number (asymmetric unit number) across a phage capsid structure in ChimeraX, using its hkcage and sym command automation tools. 
<br><br>

<h2>How to simulate your unknown phage</h2>

<h3><mark>Pre-simulation needs</mark></h3>

- You will need to know you phage genome length.
- You will need your phage genome annotated and proteins folded for use. To do this, visit [Pharokka](https://github.com/gbouras13/pharokka), [Phold](https://github.com/gbouras13/phold), [Phynteny](https://github.com/susiegriggo/Phynteny) for genome annotation and protein identification. For the full process access the [notebook](https://colab.research.google.com/github/gbouras13/phold/blob/main/run_pharokka_and_phold_and_phynteny.ipynb). Then visit [AlphaFold2](https://github.com/google-deepmind/alphafold) and [ColabFold](https://github.com/sokrypton/ColabFold) for protein folding.
- Have a possible understanding of asymmetric unit structure, if your predicting a model larger than a T#=1 capsid size. 
- Have downloaded UCSF ChimeraX to your working computer.
<br><br>
<h3><mark>STEP 1 - Define your unknown phage T# and protein copy number</mark></h3>

1. Define your T-number (T#)

   Using your genome length, define your T# using the parameters below (Luque et al., 2020). Main sizes for icosahedral symmetry, access more quasi-symmetry capsid sizes and associated lattice types in supplementary document folder.

   Sizes defined by the following where G is your genome length, T is your T#, and D is your capsids diameter:
<br><br>
<p align="center">
   $$G(T) = a_G T^{b_G}$$    where    $$D(T) = a_D T^{b_D}$$
</p>
<br><br>
<p align="center"><strong>TABLE 1: Genome length proportional to T#</strong></p>

<div align="center">
  
   | T#          | lower limit (kbp)  | Upper limit (kbp) |        
   |-------------|--------------------| ------------------|          
   | 1           | 1.2401731          | 4.412216004       |
   | 3           | 8.112244379        | 17.09526687       |
   | 4           | 13.20724825        | 24.48067158       |
   | 7           | 33.50795485        | 50.07269832       |
   | 9           | 50.05269322        | 70.22104642       |
   | 12          | 77.24829866        | 106.0778193       |
   | 13          | 86.65958139        | 119.6687262       |
   | 16          | 115.5272068        | 165.3666741       |
   | 19          | 145.2220842        | 218.1227542       |
   | 21          | 165.4641966        | 256.9938435       |
   | 25          | 206.9939534        | 343.1382484       |
   | 27          | 228.2632678        | 390.244288        |
   | 28          | 239.0191922        | 414.7751593       |
</div>
  
   Note: 
   - T#s can overlap in genome size and bps number eg T=3 and T=4. In this scenario consider which T# is most common or stable for your phage family type or bps length, based on literature. If literature review doesn't help determine the best T# for you, consider setting up all possible versions for visualisation and observational review.
   - The type of DNA/RNA your phage has will also help to define its size, with dsDNA requiring a higher T# to support a larger genome.
   - Phage capsid size and proteomics can also help define. See more in supplementary documents folder.
   - See [The Missing Tailed Phages: Prediction of Small Capsid Candidates](https://pubmed.ncbi.nlm.nih.gov/33302408/) for more information on how these sizes were defined. 
<br><br>

2. Define your T# parameters for use in simulation.

   The CK formula uses (h, k) parameters to define the T# based on symmetry. Therefore, knowing your T#, you can work backwards to determine what these will be. These will then be used to create your hkcage in ChimeraX. Example: for a    T# of 1 your (h, k) values would be (1, 0) where 1 = 1^2 + 1x0 + 0^2. In this sense you can work to find yours. Here are a few examples: 

<p align="center">
   $T_i(2, 1) = 2^2 + 2 \times 1 + 1^2 = 7$
</p>
<p align="center">
   $T_i(3, 0) = 3^2 + 3 \times 0 + 0^2 = 9$
</p>
<p align="center">
   $T_i(3, 1) = 3^2 + 3 \times 1 + 1^2 = 13$
</p>

  Use the following equations to define your h, k, parameters

<p align="center">
  $$
  h = \frac{-k \pm \sqrt{4T - 3k^2}}{2}
  $$
</p>

<p align="center">
  $$
  k = \frac{-h \pm \sqrt{4T - 3h^2}}{2}
  $$
</p>


3. Define your protein copy number

   The rules of icosahedral symmetry indicate an increase of 1 for your T#, would see an increase of 60 asymmetric units. Following this rule, a T=1 will have 60 identical units (asymmetric units for T numbers greater then 1), a T=3 would have 180, and a T=13 would have 780 asymmetric units.

   Based off this thinking, use your T# to determine how identical units you will see when creating your sym in ChimeraX. 
<br><br>
<h3><mark>STEP 2 - Simulate your phage structure in UCSF ChimeraX</mark></h3>

   _Follow instructions below using test case_

1. If you don't have ChimeraX installed, download the [latest copy](https://www.cgl.ucsf.edu/chimerax/download.html) and install
2. Open ChimeraX
3. Open your capsid protein .pdb file 

```bash
   open 1CD3
   ```

   Notes:
   - You can open your file using ChimeraX command line, or Finder.
   - Use 'open ~/Desktop/.../file_location/file_name.pdb' for local files, or 'open 1CD3' for [RCSB PDB Protein Data Bank](https://www.rcsb.org/) files.
   - Multiple proteins can be open in the same working file, at the same time.

<p align="center">
<img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/7f9c7ada-7bc8-422d-bca0-8d5722cf951e" />
</p>
<p align="center">
  Figure 4: View of Protein 1CD3 opened in ChimeraX, acessed from PDB Data Bank.
</p>
<br><br>

4. Save session as a working .cxc file. Complete by pasting the below in the command line or through the main menu by File > Save. 

```bash
   save session
   ```

  Notes:
  - You will know this has worked, when displayed in your log panel to the right hand side of your screen in ChimeraX.
<br><br>

5. Create your hkcage. Copy and paste the following code into the command line of ChimeraX (Default)
   
```bash
   hkcage 1 0 radius 120.0 edgeRadius 1.0 orientation '222' sphereFactor 1.0 alpha hexagonal color white
   ```

   Where:
   - **hkcage (h,k)** is your defined parameters for your T# e.g. _hkcage 1 0_ sets up a T=1 capsid size based on (h,k)=h2+hk+k2. See above. 
   - **Radius** increases and decreases size of the hkcage to support your surface area, density and protein size needs. If wanting to increase size, reuse the same command line as above but include _replace true_ at the end to overwrite the initial hkcage structure. Default size 120.0. Notes: ChimeraX works in Angstroms for physical distance units.
   - **Edge radius** how thick you want your hkcage axis to be. Default 0.5.
   - **Orientation** determines your symmetry type i.e. 222 for icosahedral symmetry with 2 fold symmetry at the x, y and z axis. Default 222.
   - **Sphere factor** determines how ‘spherical’ you want the icosahedral shape, with 1.0 being the most spherical like, and 0.0 being most icosahedral like (i.e. can see where the pentagons fold for the icosahedral shape). 
   - **alpha** determines lattice type. For lattice types see here. Default hexagonal.
   - **color** the colour of your hkcage. Default white.

   For more information on the parameters you can change, visit [ChimeraX hkcage](https://www.cgl.ucsf.edu/chimerax/docs/user/commands/hkcage.html) and [UCSF ChimeraX User Guide](https://www.rbvi.ucsf.edu/chimerax/docs/user/index.html) 

<p align="center">
<img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/6fc77ce2-6b3f-450c-aff1-4c338b156ec0" />
</p>
<p align="center">
  Figure 5: hkcage development rendering of T=1 capsid shell using default command code. View of 2 different angles.
</p>
<br><br>

6. Place protein on your hkcage at site of one of the side axis of a pentagon to enable simulation.

   This step is done manually using the right mouse tools located in the top main menu bar. To do this:
   - activate the protein in your model ID pane by checking the _green finger check box_ to select.
   - select the _move model_ button in the right mouse tools main menu, and while holding down _command_ (on Mac) or _alt_ (on Android) move the protein to the position you need it to be. Holding command or Alt enables you to isolate the protein model from your other layers.
   - once in place on your pentagon, select the _rotate model_button and while holding down _command_ (on Mac) or _Alt_ (on Android) rotate your mouse curser close to the edge of your screen. This will rotate around the axis. If needed you can change the rotation axis by moving diagonal or straight across the screen. 

   Tip:
     - It will help with placement if you have some understanding of your proteins orientation or oligomeric state.
     - If you capsid structure is greater than a T=1, then you will need to place your asymmetric unit, or if separate, your required number of proteins in the hexamer also to enable simulation. i.e - if a T=1 then just the pentamer, if T=2 then one protein in the pentamer and 1 in the hexamer, or T=3 then 1 in pentamer and 2 in the hexamer, and so on.

<p align="center">
<img width=80% height=auto alt="image" src="https://github.com/user-attachments/assets/2d60448e-31b3-4ea5-a09d-b215a82de5d7" />
</p>
<p align="center">
  Figure 6: protein placement of 1CD3 assymetric unit on T=1 hkcage pentamer axis to enable simulation. LHS - top down view of 1CD3 on the T=1 hkcage, RHS - side view of 1CD3 T=1 hkcage protein placement.
</p>
<br><br>
 

7. Sym your units across your hkcage. Copy and paste the following code into the command line of ChimeraX (Default)

```bash
   sym #2 #1 i,222
   ```
   Where:
   - #1 is your hkcage model ID
   - #2 is your protein structure model ID
   - i indicates your icosahedral symmetry
   - 222, is 2-fold at x,y,z symmetry

Tip/s and notes:
   - If simulating more than 1 unit at a time, the use the command line sym #2,3 #1 i,222, where#2,3 are your protein model IDs. 
   - For different symmetry and fold types see [UCSF ChimeraX Sym command page](https://www.cgl.ucsf.edu/chimerax/docs/user/commands/sym.html).
   - Once sym'ed, press control on your keyboard to deselect the units selected.
   - Sym's can take time to process and set-up by your computer. It is not unusual for it to take a few mins for the sym to show.

<p align="center">
<img width="748" height="243" alt="image" src="https://github.com/user-attachments/assets/b8637622-6a8a-42cc-86f5-74bcc216086e" />
</p>
<p align="center">
  Figure 7: 1CD3 protein assymetric unit simulated across the T=1 hkcage. LHS - pentamer face view, RHS pentamer view side on.
</p>

8. Extend your predictive model with further proteins:

   a. to enable another sym - open new .pdb file, move and place the new protein where required, then run sym again with new model IDs and symmetry types. Note: the more syms in a working file the more time it will take to render. Once rendered, save as a new file to reduce lagging and glitches. 


   b. for addition of associated proteins e.g. tail - open new .pdb file, move and place the new proteins manually. 
<br><br>

<h3><mark>Further command considerations<mark></h3>
   - Use molecule styles to render your proteins the way you need them i.e. to show ribbon use _cartoon_. Find more options here. 

```bash
   show cartoon hide surfaces hide atoms
   ```

   - Colour by protein ITPM confidence level using command _color bfactor palette alphafold_

```bash
   color bfactor palette alphafold
   ```

   - Include [XYZ-axis](https://www.rbvi.ucsf.edu/chimerax//docs/user/formats/bild.html#:~:text=BILD%20is%20a%20simple%20text,measure%20inertia%2C%203D%20object%20formats) for easier capsid/hkcage orientation. Noting X is red, Y is yellow, and Z is blue.
<br><br>


<h2>Version log</h2>
PholdAPhage is a novel method to unknown phage development in 2025. Current release V1.
<br><br>

<h2>Bugs and suggestions</h2>
If you come across bugs with PholdAPhage, or would like to make any suggestions to improve the method, please open an issue or email renee.green@flinders.edu.au .
<br><br>

<h2>Acknowledgements</h2>
Molecular graphics images were produced using the UCSF ChimeraX package from the Computer Graphics Laboratory, University of California, San Francisco (supported by NIH P41 RR-01081). Annotation analysis and protein folding to support development of this methods completed using Pawsey Supercomputing Research Centre (Perth, Australia) which is funded by the Australian Government. 
<br><br>

<h2>How to cite</h2>

If you use **PholdAPhage**, I would recommend a citation in your manuscript along the lines of:

All predictive modelling of phages were done using the PholdAPhage predictive modelling protocol (Green, R. G. (2025), **PholdAPhage**: [https://github.com/reneegreen816/PholdAPhage](https://github.com/reneegreen816/PholdAPhage/edit/main/README.md) ). 
 
Is you use Pharokka, Phold, Phynteny, or AlphaFold2 and collabfold for pre-simulation needs, it would be recommended to also include:

Genome annotations completed with Pharokka V1.8.0 (Bouras, et al. 2023),  Phold V1 (Bouras, et al. 2025), and Phynteny (Grigson, et al 2025). Folds completed with AlphaFold2, with oligomeric predictions completed with Phlegm (Grigson, et al 2025). Predictive modelling and simulation completed by UCSF ChimeraX package and sym command tools by the Computer Graphics Laboratory, University of California, San Francisco, and UCSF ChimeraX package hkcage command by Luque Lab at San Diego State University, with funding from the NSF.

With the following full citations for the constituent tools below where relevant:

- George Bouras, Roshan Nepal, Ghais Houtak, Alkis James Psaltis, Peter-John Wormald, Sarah Vreugde, Pharokka: a fast scalable bacteriophage annotation tool, Bioinformatics, Volume 39, Issue 1, January 2023, btac776, https://doi.org/10.1093/bioinformatics/btac776
- Grigson, S.R., Bouras, G., Papudeshi, B., Mallawaarachchi, V., Roach, M.J., Decewicz, P., & Edwards, R.A. (2025). Synteny-aware functional annotation of bacteriophage genomes with Phynteny. bioRxiv, 2025.07.28.667340. https://doi.org/10.1101/2025.07.28.667340.
- Jumper, J. et al. “Highly accurate protein structure prediction with AlphaFold.” Nature, 596, pages 583–589 (2021). DOI: 10.1038/s41586-021-03819-2
- Pettersen, E.F., Goddard, T.D., Huang, C.C., Couch, G.S., Greenblatt, D.M., Meng, E.C., and Ferrin, T.E. "UCSF Chimera - A Visualization System for Exploratory Research and Analysis." J. Comput. Chem. 25:1605-1612 (2004). http://www.cgl.ucsf.edu/chimera
- Mirdita, M. et al. “ColabFold: Making protein folding accessible to all.” Nature Methods, 19, pages 679–682 (2022). DOI: 10.1038/s41592-022-01488-1

<h2>References</h2>

- Comas-Garcia, M. (2024). How structural biology has changed our understanding of icosahedral viruses. Journal of Virology, 98(10). https://doi.org/10.1128/jvi.01111-23
- Icosahedric capsids, Caspar and Klug ~ ViralZone page. (2019). Expasy.org. https://viralzone.expasy.org/8577
- Luque, A., Benler, S., Lee, D. Y., Brown, C., & White, S. (2020). The Missing Tailed Phages: Prediction of Small Capsid Candidates. Microorganisms, 8(12), 1944. https://doi.org/10.3390/microorganisms8121944

