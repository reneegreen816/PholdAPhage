# PholdAPhage

<p align="center"> 
  <img width=35% height=auto alt="image Phages being folded" src="https://github.com/user-attachments/assets/5eac2c23-ecb9-48d6-9bc2-ec433d377eea" />
</p>


Assemble unknown phage particles one protein at a time.

**_PholdAPhage_** is a predictive modelling tool for the quick, efficient visualisation of unknown phage structures for experimental baseline. Traditional wet lab experiments to define protein morphology are time consuming and expensive. PholdAPhage supports the three dimensional reconstruction of unknown phage structures, utilising AlphaFold2, oligomeric state prediction, and predictive simulation by ChimeraX. 
<br><br>

<h2> Table of contents</h2>

- Background
   - What is a phage?
   - How does PholdAPhage work?
- Brief Overview
   - Novel method
- How to simulate your unknown phage
   - Presimulation needs
   - Protocol - Step 1 - Define your unknown phage T# and protein copy number
   - Protocol - Step 2 - Simulate your phage structure in ChimeraX
   - Further command considerations
- Version Log
- Bugs and Suggestions
- Acknowledgements
- How to cite
<br><br>

<h2>Background</h2>

**What is a phage?**

Bacteriophages (phages) are viruses which infect bacteria and are the most abundant and diverse biological agents on earth. They consist of three main components: a capsid protein head, a nucleic acid genome, and tail for bacterial interaction. Presenting therapeutic opportunities as viral vectors and antimicrobials, many of their structures are unknown, with head and tail composition different for each phage. Structural differences which pose challenges in understanding their molecular composition and application for phage therapy. PholdAPhage provides a novel approach to structurally modelling unknown novel phages for baseline and visualisation.

**How does PholdAPhage work?**

Phage capsid structures are highly conserved, 96% are icosahedral in nature applying mathematical principles of symmetry to shape their protein capsids proportional to genome length. PholdAPhage exploits this evolutionary capsid design principle, employing symmetry type and genome length, to predict an unknown phages triangulation number (T-number or T#), for protein copy number in support of computational simulation. 
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
  <img width=80% height=auto alt="image Casper-Klug formula" src="https://github.com/user-attachments/assets/3fce8eaa-7787-44c4-8c60-4c9758d3f2f4" />
</p>
<p align="center">
  Figure 2: Casper-Klug formula for viral symmetry to determine T-number and capsid protein copy number. The theory is built on 60 identical subunits organized on the 20 triangles creating the faces of the icosahedral shape.
</p>
<br><br>
Example: A phage genome length of ~5,000bps is typical to a phage capsid T# of 1. A T=1 capsid incorporates 60 major proteins (protein copy number) simulated across the capsid structure, displaying the hkcage parameters (h, k) as (1, 0) for T# (1, 0) = 1^2 + 1x0 + 0^2 = 1. More infromation at [Viral Zone](https://viralzone.expasy.org/8577)
<br><br>

<h2>Brief overview</h2>

**Novel method**
<!--<br><br>
<img width=100% height=auto alt="image" src="https://github.com/user-attachments/assets/391993b5-6674-49e5-891c-766dc3367faa" />
<br><br>-->
<img width=100% height=auto alt="image" src="https://github.com/user-attachments/assets/73cbb970-c9e8-4f32-a47d-26bcb74b4c97" />
<br><br> 

Using the Casper-Klug (CK) Theory of viral symmetry:
- Step 1: defines your phage's capsid T# by using the Genome-to-T-number model.
- Step 2: takes your defined T# and (h, k) parameters to simulate your protein copy # (assymetric unit number) across a phage capsid structure in ChimeraX, using it's sym command automation tool. 
<br><br>

<h2>How to simulate your unknown phage</h2>

**<mark>Pre-simulation needs</mark>**
- You will need to know you phage genome length.
- You will need your phage genome annotated and proteins folded for use. To do this, visit [Phold](https://github.com/gbouras13/phold), [Phyntenny](https://github.com/susiegriggo/Phynteny), and [ColabFold](https://github.com/sokrypton/ColabFold).
- Have an understanding of assymetric unit structure if greater then a T=1 phage capsid size. 
- Have downloaded ChimeraX to your working computer.

<br><br>
**<mark>STEP 1 - Define your unknown phage T# and protein copy number</mark>**

1. Define your T-number (T#)

   Use your genome length (in bps) to determine your T#. If you know your phage capsid diameter, this can also help with genome length proportional to cappsid size. To determine your phages T# you can start with the following links. If the phage is known or proteomics are known, this can also help. 

   - [The Missing Tailed Phages: Prediction of Small Capsid Candidates](https://pmc.ncbi.nlm.nih.gov/articles/PMC7762592/)
   - link 2
   - link 3 
  
   Note: 
   - Some T#s can overlap in genome size / bps number. In this sennario, consider which T# is most common, stable for your phage type, based on litrature. If decision is not able to be made, consider setting up all possibile versions for visuliasation and review. 


2. Define your T# parameters for use in simulation.

   The Casper-Klug formula uses (h, k) parameters to define the T# based on symmetry. Therefore, knowing your T#, you can work backwards to determine what these will be. These will then be used to create your hkcage in ChimeraX.


   For example: for a T# of 1 your (h, k) values would be (1, 0) where 1 = 1^2 + 1x0 + 0^2. In this sense you can work to find yours. Here are a few examples: 

   - T#7 or (2 ,1) = 2^2 + 2x1 + 1^2 = 7
   - T#9 or (3 ,0) = 3^2 + 3x0 + 0^2 = 9
   - T#13 or (3 ,1) = 3^2 + 3x1 + 1^2 = 13


   Following this same train of thought, work back from your T# to determine your formula parameters. 
   

3. Define your protein copy number

   The rules of geometric icosahedral symmetry indicate an increase of 1 for T# would see an increase of 60 asymmetric units. Following this rule, a T=1 will have 60 identical protein units (or asymmetric units for T numbers greater then 1), a T=2 would have 120, and a T=13 would have 780 asymmetric units.

   Based off this thinking, use your T# to determine how many major capsid proteins (or assymetric units) you will see when sym'ed in ChimeraX. 

<br><br>
**<mark>STEP 2 - Simulate your phage structure in ChimeraX</mark>**

   _Follow instructions below using test case_

1. If you don't have ChimeraX installed, download the [latest copy](https://www.cgl.ucsf.edu/chimerax/download.html) and install it.
2. Open your capsid protein .pdb file 

```bash
   open 1CD3
   ```

   Note/s:
   
   - Use 'open ~/Desktop/.../file_location/file_name.pdb' for local files, or 'open 1CD3' for PDB bank files.
   - Multiple proteins can be open in the same working file at once.

3. Save session as your working file. Complete by pasting the below in the command line or through the main menu by File > Save.

```bash
   save session
   ```

4. Create your hkcage. Copy and paste the following into the command line of ChimeraX (Default)
   
```bash
   hkcage 1 0 radius 120.0 edgeRadius 1.0 orientation '222' sphereFactor 1.0 alpha hexagonal color white
   ```

   Where:
   - **hkcage (h,k)** is your parameters for T# e.g. _hkcage 1 0_ sets up a T=1 capsid size based on (h,k)=h2+hk+k2. See above. 
   - **Radius** increases and decreases size of the hkcage to support your surface area, density and protein size needs. If wanting to increase size use the same command line as above but include _replace true_ at the end to overwrite the initial hkcage structure. Default 120.0
   - **Edge radius** how thick you want your Hkcage axes to be. Default 0.5
   - **Orientation** determines your symmetry type i.e. 222 for icosahedral symmetry with 2 fold at the x,y and z axis. Default 222
   - **Sphere factor** determines how ‘spherical’ you want the icosahedral shape, with 1.0 being the most spherical like, and 0.0 being most icosahedral like (ie can see where the pentagons create the icosahedral shape).
   - **alpha** indicates lattice type. For lattice types see here. Default hexagonal
   - **color** colour of your hkcage. Default white  

   For more information on the parameters you can change, visit here and here. 

5. Place protein on your hkcage at site of one of the pentagons to enable simulation.
   
   This step is done manually using the right mouse tools located in the top main menu bar. To do this you will need to have some understanding of your proteins orientation and oligomeric state.

6. Sym your protein across your hkcage. Input command string into ChimeraX command line (Default)

```bash
   Sym #1 #2 I,222
   ```
   Where:
   - #1 is your protein structure model ID
   - #2 is your hkcage model ID
   - i indicates icosahedral symmetry
   - 222, is 2 fold at x,y,z symmetry

   For different symmetry and fold types see [ChimeraX Sym command page](https://www.cgl.ucsf.edu/chimerax/docs/user/commands/sym.html).

7. Extend your predictive model with further proteins:

   a. to enable another sym - open new pdb file, move and place the new protein where required, then run sym again with new model IDs and symmetry types. Note: the more syms in a working file the more time it will take to render. Once rendered, save as a new file to reduce lagging and glitches. 

   b. for addition of associated proteins e.g. tail - open new pdb file, move and place the new proteins manually. 

<br><br>
Further command considerations:
   - Use molecule styles to render your proteins the way you need them i.e. to show ribbon use _cartoon_. Find more options here. 

```bash
   cartoon
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



