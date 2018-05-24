# How to Run the Codes on this system

## Overview
Following is a broad overview of what is included in the install file, and why they were included. Links to these codes can be found in the install document. This is the install order I followed on my system.

#### Core Programs
- VirtualBox Guest Additions - this allows us to more easily use the virtual box and adds lots of great tools
- Anaconda - This is arguably the best way to manage Python, and will give us a solid foundation for the madness we'll do next

#### Languages
After we have Jupyter, we can cram in a host of programming languages/environments with their Jupyter kernels. After we get them all in Jupyter, we'll add some other tools for working with them, like dedicated IDEs.
- Python 2.7 - Often, code is still written in Python 2, so having an environment to work in this version of Python makes sense
- SageMath - This is a powerful scripting language built on Python that integrates LaTeX and strong math support to be a truely viable open alternative to Mathematica. Since this is the main reason I started this project, I add it first.
- Machine Learning (py) - Google's python libraries for machine learning (TensorFlow, Keras, SciKitLearn)
- R - A long-time staple in scientific computing, it still has uses where it shines
- Gnuplot - A plotting tool used by some of the other tools below. It's nice to be able to directly write code for it.
- Octave - A long-time contendor as an open Matlab alternative. It emphasizes matching Matlab syntax, so usually you can copy-paste code between the two and they run just fine.
- Scilab - Another contendor as an open Matlab alternative. It focuses less on matching Matlab syntax, and so has been able to add a lot of functionality and tools. Another favorite of mine.
- Julia - Looks to be a powerhouse, modernizing scientific computing with a host of powerful tools.
- bash - Born-Again SHell is what the Linux terminal uses. It can be nice to be able to write it and run it in Jupyter.
- Ruby - Ruby is a popular language that makes a lot of science tasks really easy. Especially because somebody has already pre-packaged a science-minded distro.
- C - Most of the time, I program microcontrollers and hardware using C, so I want to be able to play with it in Jupyter
- C++ - A long-time staple of scientific computing. This kernel lets you run it almost as though it was interpreted, rather than compiled, which is neat.
- C# - Can't leave it out if we have all the other C's, right?
- Fortran - One of the most powerful languages to exist, it is still used for regorous math, and many older coldes (like those used in nuclear) are in Fortran.
- Perl 6 - Perl is an interpreted language that can do what many languages above cannot.
- Haskell - I heard a story once about how Haskell would be an ideal cryptocurrency contracting language, and I was intrigued enough to include it here to play with
- Common Lisp - Honestly, just included because it's so weird
- BeakerX - Basically a Java-esque toolkit that includes:
  - Clojure - A flavor of Lisp with powerful macros. This means that unless you want to mess with setting up Common Lisp, you can have lisp with one easy command!
  - Groovy - a Java-syntax-compatable, programming and scripting language that can use Java codes and libraries
  - Java - a common tool for programming. Like C++, this can be run as a quasy-interpreted language
  - Kotlin - a language that runs on the Java virtual machine and can be compiled to JavaScript or compiled using LLVM compiler
  - SQL - allows us to create and manipulate databases. THis SQL is set up to work with a Java system, so you can use well established methods for managing databases
  - Scala - appears to be the "better version" of Java, created to be like Java, but address problems people had with Java

So we can edit outside of Jupyter, we grab some text editors and IDEs 
- Atom – GitHub's own text editor. Lots of community-created tools to play with here, including an ide plugin that lets us run code from the editor
- Sublime – a wildly popular text editor with lots of tools and plugins, including linter, which lets us run code from the editor
- VIM (spf13) - a long-standing staple in computer programming. This is a terminal-based text editor. I felt like I should learn it because it's so widely known
- Code::Blocks, Eclipse, QT - common IDEs with plugins for many languages.
- Language-specific IDEs:
  - Python: Spyder, PyCharm - python is THE main language for scientific computation it seems. These two come highly recommended
  - R: RStudio - A powerful R IDE
  - Others still pending.

#### Simulation/Design Tools
##### Computational Fluid Dynamics (CFD)
- OpenFOAM - A staple in open CFD.
- Visual-CFD (OpenFOAM GUI) - Anything that makes OpenFOAM easier to use is a plus
- SU2 - OpenFOAM actually suffers from a host of problems. SU2 has different problems, but usually one of the two can do what you need.
- Salome - a general workbench for multiple modeling codes, including FEA below

##### FEA
- Code_Aster - Seems to be the main one for Linux
- Code_Aster GUI - Again, anything to make Code_Aster easier to use is a plus

##### Circuits
- Eagle - I've actually made circuit boards that were printed using this tool
- The following were on an [Engineering with Linux](https://help.ubuntu.com/community/UbuntuEngineering) page. As I play with them, I'll cut down to the ones I use:
  - gEDA
  - KiCad
  - Qucs
  - Fritzing

##### Nuclear
- OpenMC - Seems it can do pretty much anything MCNP can do, and some of that more easily
- DRAGON - Another code I found

##### CAD/3D modeling
- FreeCAD - Seems to be the most advanced, freely-available CAD package out there
- Blender - A standard for 3D animation and modeling, it's relatively easy to learn and quite powerful

##### Aerospace
- XFoil - I used this in designing a drone, and it's not too bad for airfoil analysis

#### Other useful engineering tools
- LaTeX - A staple in document writing and type-setting. Several Jupyter installs (like SageMath) depend on it to get pretty formatting, and any engineering box should have an install. That said, I usually use Overleaf or ShareLaTeX.
- RAVEN - An exceptionally powerful parametric and probabilistic analysis tool and flow manager that can be used to test sensitivity of variables in almost any code
- MOOSE - A powerful coupled-equation, multi-physics solver that has found heavy use in nuclear, but which can do FEA, CFD, material science, and anything else. At its core, it solves coupled partial differential equations.
- Mendeley, Zotero - Reference managers that allow you to download, organize, annotate, and share references and papers, and which simplify citation in a host of ways.

#### The rest
- VLC - Can play any media under the sun
- Bunch of things...I haven't gotten here yet

## How to run and update everything
#### Core Programs
- VirtualBox Guest Additions - 
- Anaconda - 

#### Languages
- Python 3.x - 
- Python 2.7 - 
- SageMath - 
- Machine Learning (py) - 
- R - 
- Gnuplot - 
- Octave - 
- Scilab - 
- Julia - 
- bash - 
- Ruby - 
- C - 
- C++ - 
- C# - 
- Fortran - 
- Perl 6 - 
- Haskell - 
- Common Lisp - 
- BeakerX - 

Text Editors / IDEs and their plugins
- Atom – 
- Sublime – 
- VIM (spf13) - 
- Code::Blocks, Eclipse, QT - 
- Language-specific IDEs:
  - Python: Spyder, PyCharm - 
  - R: RStudio - 
  - Others still pending.

#### Simulation/Design Tools
##### Computational Fluid Dynamics (CFD)
- OpenFOAM - 
- Visual-CFD (OpenFOAM GUI) - 
- SU2 - 
- Salome - 

##### FEA
- Code_Aster - 
- Code_Aster GUI - 

##### Circuits
- Eagle - 
- The others:
  - gEDA
  - KiCad
  - Qucs
  - Fritzing

##### Nuclear
- OpenMC - 
- DRAGON - 

##### CAD/3D modeling
- FreeCAD - 
- Blender - 

##### Aerospace
- XFoil - 

#### Other useful engineering tools
- LaTeX - 
- RAVEN - 
- MOOSE - 
- Mendeley, Zotero - 

#### The rest
- VLC - 
- Bunch of things...I haven't gotten here yet
