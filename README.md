## Overview
Engineering in Linux is a step-by-step guide to setting up a Linux Virtual Box for engineering work. It's targeted towards engineers who can run a computer, but who don't spend large amounts of their time learning about them (i.e. mechanical, chemical, electrical, and nuclear engineers). The hope is that this can provide a powerful toolkit for engineers to start coding or developing quickly without having to waste large amounts of time setting things up. Development of this project began when I found [SageMath](http://www.sagemath.org), distributed as a CentOS virtual box. I soon wanted more language support, and realized that starting from a clean Ubuntu install would be the easiest way to get repeatably get the system I wanted.

It starts by installing a ton of programming languages, and hooking them all into Jupyter via kernels. This provides a single development interface and similar behavior for multiple languages, allowing me to focus on learning and using the languages and not fiddling with multiple design environments. Following Jupyter integration, several text editors are added and configured for the languages installed, again to provide a unified coding interface for all languages. Acknowledging that having an Integrated Development Environment (IDE) for the languages I plan to use often provides additional functionality and utility, I then add several IDEs. By the end of this portion, I have multiple options for writing in over 20 languages, and I have several IDEs all using the same environments so I don't have to configure a bunch of them.

After the general programming things are set up and work, I install more engineering-specific codes. Not all of these tools would be commonly used by all engineering disciplines, but I have worked in mechatronics, aerospace, and nuclear engineerings, giving me a broad exposure to many engineering tasks that I want to be able to handle in this system. I include some Finite Element Analysis (FEA) and Computational Fluid Dynamics (CFD) for stress and flow analyses. I then included some circuit design and analysis tools for mechatronics or similar work. I include some 3D creation tools (CAD, Blender) for creating 3D printing shapes or rough design work. I add some aerospace (airfoil) and nuclear (neutronics and particle transport) codes as well because I plan to use them.

After all these tools are set up and functional, I add additional useful tools, like reference managers; editors for images, audio, and video, media players, etc. I end by adding a powerful probabalistic analysis tool and a coupled equation solver that are often used in my school and which are quickly becoming the standard software for what they do. They are powerful and general tools that can benefit any engineer.

The project will have several things, detailed below:
1. A 'How to Run' file that describes in detail what every code for and how to start it up. I suggest you hit this one first to see what you'd want to install.
2. An install file that contains a step-by-step guide to how everything was installed, including references for everything useful that I looked at to figure out how to install the code.
3. Images (like kernel logos) and such that I create while setting this up
4. Later, I'd like to create an install script that will automatically install everything you select in whatever location you choose.
5. Eventually, I'd like to include example files that show the neat things that can be done in all the different languages. As I'm installing mostly "scientific" versions of these tools, I suspect that a a couple of really good examples can be programmed in multiple languages.

## Specific codes
### Languages
Python 3 in installed via Anaconda, which gets us Jupyter. We then add the following languages:
- Python 2.7
- SageMath
- Machine Learning (py)
- R
- Gnuplot
- Scilab
- Octave
- bash
- Ruby
- Perl 6
- C/C++/C#
- Julia
- Fortran
- Haskell
- Common Lisp
- BeakerX, which includes:
  - Clojure
  - Groovy
  - Java
  - Kotlin
  - SQL
  - Scala

### IDEs
Text Editors
- Atom, with ide plugin
- Sublime, with linter
- VIM (spf13)
General, "flexible" IDEs (that can have multiple languages in them):
- Elipse
- Code::Blocks
Specific IDEs
- Sypder, PyCharm
- RStudio
- ...

### Simulation/Design Tools
CFD
- OpenFOAM
- Visual-CFD (OpenFOAM GUI)
- SU2
FEA
- Code_Aster
- Code_Aster GUI
Circuits
- Eagle
- gEDA
- KiCad
- Qucs
- Fritzing
Nuclear
- OpenMC
- DRAGON
CAD/3D modeling
- FreeCAD
- Blender
Aerospace
- XFoil

### Other useful engineering tools
- LaTeX
- RAVEN
- MOOSE
- Mendeley, Zotero ref managers

### The rest
- VLC
- Bunch of things
