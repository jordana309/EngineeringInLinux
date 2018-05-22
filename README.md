# EngineeringInLinux
# EngineeringInLinux
Explanation and General Notes
Anything in mono typeface in this document is to be what is typed into the terminal.

How to run things – Incomplete. TODO after install.
We’ve got several tools pre-configured on this box. We needed to have several python environments, so to run them usually you need to switch to the right profile. When you log in, you can open the terminal with Ctrl+Alt+t, from the Ubuntu logo (analogous to the “Start Menu”), or with the terminal button on the taskbar.

First, there are a bunch of regular apps installed (see Explanation above), which you can search for in the “Start Menu”. However, there are a few programs that require a little extra effort, which is explained below.

Jupyter (regular programming-type things)
1.	Set the Python profile: source activate base
2.	Run Jupyter: jupyter notebook
3.	This will create a key’ed instance of notebook, and auto log you in to a browser.
4.	From here on, you’ll be in notebook, and won’t type anything directly into the terminal.

RAVEN
1.	Set the Python profile: source activate raven_libraries
2.	Create your input file (.xml), and set that up. The directory where this .xml sits is your “project directory”
3.	cd your/project/directory
4.	run: ~/Codes/raven/raven_framework inputFileName.xml

MOOSE
1.	Set the Python profile: source activate moose
2.	nano ~/.bashrc
a)	Remove the # in front of the following lines:
export CC=mpicc
export CXX=mpicxx
export F77=mpif77
export FC=mpif90
export PATH=$GCC_HOME/bin:$MPI_HOME/bin:$PATH
3.	cd your/project/directory
4.	Write your script, stork it, write the header and .c file, then run your cases.
5.	When you are done with MOOSE, you need to again comment out the lines in bashrc to make sure everything else works (like SageMath or Fortran, for example). These compilers are customized for MOOSE, and pretty much break anything else that needs any of those compilers.


Updating things – Very incomplete. TODO later.
Base OS and Packages
1.	When you start up the system, codes registered with the app manager will upgrade via a GUI. This includes the system base code. However, many codes won’t update this way. For the majority of them, you can run the following script:
2.	Get updated version lists: sudo apt-get update
3.	Perform update: sudo apt-get dist-upgrade

Anaconda Python Environments
Anaconda itself is updated using the above. Each environment is updated separately, so you need to activate each one, then update the packages in it. Note: do not update the RAVEN environment unless something on their site says you should. They are particular about what version of the Python packages are used.
1.	conda activate [env]
2.	conda update --all
3.	Where [env] is the environment. You can see all environments on the system with: conda env list
4.	There are also several programs that were installed via pip, and which need to be updated using pip. Do that with the following command, where [pak] is from the list below: pip install --upgrade [pak]
a)	

RAVEN
1.	cd ~/Codes/raven
2.	git pull
3.	To compile and and rerun the tests (don’t forget that you need to be in the raven_libraries environment!):
4.	make
5.	./run_tests

MOOSE
1.	cd ~/Codes/moose
2.	git fetch origin
3.	git rebase origin/master
4.	scripts/update_and_rebuild_libmesh.sh
5.	Then, if you want to rerun the tests (don’t forget that you need to be in the moose environment!):
6.	cd test
7.	make
8.	./run_tests

SageMath
1.	~/Codes/sage/sage –upgrade

R
1.	sudo -E R
2.	update.packages()

FORTRAN
1.	

Octave
1.	Start your script with the following to make everything appear nicely in the terminal/Jupyter: graphics_toolkit("gnuplot")
2.	

Scilab
1.	

bash
1.	

Gnuplot
1.	

Perl
1.	

Haskell
1.	

Ruby
1.	

C++
1.	

C#
1.	


Install procedure
This is installed using the ubuntu-16.04.4-desktop-amd64 image.
Create a new virtual box. Give it 4+ GB of ram, 250 or so GB of hard drive space. Install Ubuntu normally. My full settings (Section → Tab). I only will note what I changed:
•	General
◦	Basic - Name: Nuke Box, Type: Linux, Version: Ubuntu (64-bit)
◦	Advanced – Shapshot Folder: [default], Shared Clipboard and Drag’n’Drop: Bidirectional
◦	Description – A programming/simulation box with multiple languages and a host of open-sourse or free coding tools, complete with a text file documenting the whole setup process.
◦	Disk Encryption – leave disabled
•	System
◦	Motherboard – Base Memory: 4096+ MB (multiples of 1024), Boot Order: remove floppy, Chipset: ICH9 [because it’s more modern, and is supposed to run a little smoother], Pointing Device: PS/2 Mouse, Extended: (checked) Enable I/O APIC, Hardware Clock in UTC Time
◦	Processor – Processor(s): 4+, Exicution Cap: 95%, leave PAE/NX off.
◦	Acceleration – Paravirtualization Interface: Default, Hardware stuff checked [default]
•	Display
◦	Screen – Video Memory: 32. Do not Accelerate (caused me problems)
◦	No other changes.
•	Storage
◦	Controller: changed Type: ICH6 [again, supposedly newer and has more options]
◦	Insert Ubuntu install disk into virtual disk drive here
•	No changes to audio, network, serial ports, usb, user interface
•	Shared Folders
◦	I have a school folder that I added here after I had installed Guest Additions. Sometimes it acts funny if you connect it before this. Make sure to check auto-mount when you add one. You can have more than one.

We are now going to install the following things:
Core programs
 
•	VirtualBox Guest Additions
•	Anaconda
 

Languages and Jupyter kernels; note that we’ll also install separate IDEs for most of these
 
•	Python 2.7
•	SageMath
•	Machine Learning (py)
•	R
•	Gnuplot
•	Scilab
•	Octave
•	bash
•	Ruby
•	Perl
•	C
•	C++
•	Julia
•	Fortran
•	Lisp
•	Haskell
•	BeakerX, which includes:
◦	Clojure
◦	Groovy
◦	Java
◦	Kotlin
◦	SQL
◦	Scala
 


Text editors / IDEs
 
•	Atom – with ide plugin
•	Sublime – with linter
•	VIM (spf13)
•	Code::Blocks
•	Eclipse
•	Spyder
•	Rstudio
 

CFD/FEA simulation tools
 
•	OpenFOAM - CFD
•	Visual-CFD – GUI for OpenFOAM
•	SU2 - CFD
•	Code_Aster - FEA
•	Code_Aster GUI - GUI for Code Aster
•	Salome - GUI for many codes
•	SimScale notes Web based
 

Nuclear simulation tools
 
•	OpenMC - MIT's neutronics code
•	DRAGON - some French guy's neutronics code
 
  
Other useful programs
 
•	Mendeley - ref manager
•	Zotero - ref manager
•	RAVEN – parametric and probabilistic analysis, program flow manager
•	MOOSE – Coupled equation multiphysics simulation and visualization
 

Ready? Let’s go!

Install VirtualBox Guest Additions
The VirtualBox Guest Additions is a toolkit that lets you copy-paste text to and from the guest system, drag files into and out of the guest system, and access shared folders between the guest and host systems. To do the latter, the current user needs to be added to the vboxsf user group, so don’t forget that.
•	Grab the kernel headers: sudo apt-get install linux-headers-generic
•	Vbox menu “Devices→Insert Guest Additions CD image...”, then select Run. Let it work. An alternative if needed (source)
•	Reboot
•	After reboot: sudo usermod --append --groups vboxsf jordan
•	Register the user group change by logging out and logging back in.

Create directory for all the installed stuff and to work out of
Things like to be put wherever, often at root. This looks really untity to me; I like them collected in one place. So, I made a Codes directory in my home folder to hold all the different codes. RAVEN and MOOSE will suggest the folder be called projects instead. Either way. Basically anything we build will go there.
•	mkdir ~/Codes
I also recommend that you create a directory for your work files, ie your code and simulation project files. I chose the one below:
•	mkdir ~/Workspace

Install Anaconda (Python)
Download version 3.X from https://www.anaconda.com/download/#download
•	Run script: bash ~/Downloads/Anaconda[version]-Linux-x86_64.sh
◦	Change install directory to ~/Codes/anaconda
◦	Install Microsoft VSCode. Why not?
•	The installer will add Anaconda Python to PATH, but you need to close and re-open the Window to register it
•	After terminal restart, update conda: conda update -n base conda
•	Add the Conda Forge channel to the bottom of our channel list so we can find packages not in the defaults channel:
◦	conda config --append channels conda-forge
◦	conda update --all
•	To create different environments, see Jupyter install below. The info below tells you how to set up both different Python environments and link them to Jupyter, and also and install multiple programming languages. Total install size for everything below is large: around XX – 12.2 GB.

Configuring Jupyter and Installing All the Development Languages
I wanted to stuff Jupyter with ALL the kernels. With the Anaconda install above, we already have a Python 3 environment ready to go. For the rest, if you’ve installed MOOSE, first comment out the MOOSE compiler information (see MOOSE under the How to Run section) to avoid problems.
Note that Jupyter Notebook will start in the current directory, and treat that directory as home (so you can drill deeper into folders, but it’s hard to go up above the starting directory). I suggest you always start it in your workspace (for me, that means I always run:
•	cd ~/Workspace
•	Start Jupyter notebook: jupyter notebook
For kernels, I’ll put the kernel we’re adding, then about how much extra space that adds (remembering that the value includes the ADDITIONAL prereqs we needed to install), and then go step-by-step on what to install. We’ll begin by adding a Python 2.7 environment (in this case, the system’s install).
•	Python 2.7 (~0.0 GB. A new environment should be ~0.6-1.5 GB) – Sometimes  code requires the older version of python, so we’ll put it in. We want to be able to run this without changing our environment, so we’ll use the system’s python2 install. Source – iPython docs
◦	python2 -m pip install --user ipykernel
◦	python2 -m ipykernel install --user
◦	If you don’t have pip for python2, then you need to first run:
▪	sudo apt-get install python-pip
▪	python2 -m pip install --upgrade pip
◦	That’s it! Python2 is now registered in Jupyter using our base install! Alternately, you could create a python2 environment using conda, and after its registered use the path to that python to install the ipykernel, but I didn’t want that much redundancy.
•	Machine Learning (~0.6 GB) – Most machine learning is done with Google’s tensorflow, so we’ll just install that the standard way. This requires that we use a different environment, and we’ll have to tweak the kernelspec so that we get it to show up as machine learning. Source – Tensorflow.org
◦	Create an environment for machine learning named machlearn with ipykernel so we can hook it to Jupyter:
▪	conda create -n machlearn pip ipykernel python=3.6
▪	source activate machlearn
◦	Check that you’ve switched: which pip (should return something in ~/Codes/anaconda)
◦	Install machine learning environment (go get the current one for python 3.6 or whichever version you picked and CPU only from here): pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.8.0-cp36-cp36m-linux_x86_64.whl
◦	Install keras (deep learning code). Source – keras.io
▪	Get HDF5 and h5py to save Keras models to disk. Sources – Stack Overflow, h5py.org
•	sudo apt-get install libhdf5-serial-dev
•	pip install h5py
▪	Get graphviz and pydot for visualization. Sources – AskUbuntu forum, Pydot GitHub
•	sudo apt-get install graphviz
•	pip install pydot
▪	Finally, install keras
•	pip install keras
◦	Install scikitlearn (datamining and data analysis, visualization tools). Source – scikit-learn.org
▪	conda install numpy scipy scikit-learn
◦	Install it in Jupyter: python -m ipykernel install --user --nam- System design and instrumentation specialist, Sustainable Energy Solutionse machlearn --display-name "Machine Learning (TF, keras, scikit-learn)"
◦	I also grabbed the three logos and cooked up my own that includes all 3 main codes. That’s in the Gifts folder on the desktop.
◦	Test it from base environment:
▪	source activate base
▪	cd ~/Workspaces
▪	jupyter notebook
•	SageMath (~10.1 GB: the tools and LaTeX and so forth: ~2.1 GB. SageMath with source code: ~8 GB installed after several hours of compiling; the binary is ~5.6 GB, but may not incorporate LaTeX, tk, etc) –  A mathematician’s notebook. Basically, it combines powerful scientific python packages with a host of other tools (including LaTeX output) for a beautiful, viable, open-source alternative to Mathematica. Sources: Sage Docs - Install from Source Sage Docs - TeX Notes, Sage GitHub, alt install method
◦	First, we are going to build from source, because that enables us to roll in LaTeX, tk, ffmpeg, and other support, as well as perhaps making better use of our virtual processors. Building takes several hours, so I note that it can also be downloaded as a binary from their website and installed (alt install method linkabove), but I’m not sure what exactly it has in it.
◦	Download pre-recs: sudo apt-get install binutils gcc g++ gfortran make m4 perl tar git openssl libssl-dev openssh-server openssh-client
◦	Get bonus codes (these make Jupyter in general and SageMath in particular more awesome. Video and image production codes, and TypeSetting code. Sources: Ubuntu LaTex Docs, Stack Exchange): sudo apt-get install ffmpeg imagemagick ghostscript texlive texlive-math-extra texlive-xetex tk tk-dev
◦	clone: cd ~/Codes
▪	git clone https://github.com/sagemath/sage.git
◦	Build it
▪	cd ~/Codes/sage
▪	export SAGE_CHECK="yes"
▪	make
◦	Change .bashrc back, and add the sage path to the end:
▪	nano ~/.bashrc
▪	Remove the # symbols in front of those lines above, and add:
# Put SageMath in our PATH and expose SageTeX for TeX
export SAGE_ROOT=/home/jordan/Codes/sage
export PATH=$SAGE_ROOT:$PATH              
export TEXINPUTS=$SAGE_ROOT/local/share/texmf:
◦	Add to the Anaconda Jupyter install (Sources: Sage forum and Stack Overflow discussions on integrating Sage with Jupyter):
▪	jupyter kernelspec install --user ~/Codes/sage/local/share/jupyter/kernels/sagemath
•	R (~0.5 GB) – A powerful, common statistical computing and graphics environment. Sources: DigitalOcean for base install; irkernel GitHub for Jupyter kernel
◦	Add key: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
◦	Add CRAN repo: sudo add-apt-repository 'deb [arch=amd64,i386] https://cran.rstudio.com/bin/linux/ubuntu xenial/'
◦	sudo apt-get update
◦	sudo apt-get install r-base libcurl4-openssl-dev
◦	Make sure that R will be able to find all packages it needs (source): nano ~/.bashrc
▪	Add the following lines at the end:
# Point R to our .pc files so that it can install properly
export PKG_CONFIG_PATH=/home/jordan/Codes/Anaconda/lib/pkgconfig
◦	Close and re-open terminal.
◦	Start R kernel as sudo (so make sure any new user will also have access to it): sudo -E R
◦	install.packages(c('repr', 'IRdisplay', 'evaluate', 'crayon', 'pbdZMQ', 'devtools', 'uuid', 'digest'))
◦	Install optional useful packages: install.packages(c('shiny', 'ggplot2'))
◦	devtools::install_github('Irkernel/Irkernel')
◦	Close the R session, and re-open not as sudo
▪	quit()
▪	R
◦	IRkernel::installspec()
•	Octave (~0.2 GB) – A scientific programming language with very MATLAB-esque syntax. It’s often referred to as the open-source MATLAB. Includes visualization tools. Sources: octave_kernel GitHub
◦	Install Octave: sudo apt-get install octave
◦	Install kernel (this also installs metakernel, and registers it with jupyter):
▪	Dependant package: pip install msgpack
▪	pip install octave_kernel --user
•	Gnuplot (<0.1 GB) – Portable, command-line graphing utility used by Octave and useful by itself. Sources: gnuplot_kernel GitHub
◦	Install gnuplot: sudo apt-get install gnuplot
◦	Install kernel:
▪	cd ~/Codes/src
▪	git clone https://github.com/has2k1/gnuplot_kernel
▪	cd gnuplot_kernel
▪	python setup.py build
▪	Needs metakernel. Suggested to install it via octave kernel above, then: python setup.py install
•	Scilab (~0.4 GB) – Similar to Octave, Scilab is an open-source MATLAB, but which focuses less on having the same syntax as MATLAB than Octave does. Includes visualization tools and many other features. Included because it has more features than Octave, and is better though out for some applications. Sources: scilab_kernel GitHub
◦	Install SciLab: sudo apt-get install scilab
◦	Install kernel (installs metakernal and kernelspec):  pip install scilab_kernel --user
•	bash (~0.0 GB) – The main command line for linux. This kernel will let you write scripts and test them in a notebook environment. Be careful when using it—it is the same as running it in the terminal window, but with syntax highlighting, so doing the wrong thing can really mess things up. Sources: bash_kernel GitHub
◦	pip install bash_kernel --user
◦	python -m bash_kernel.install
•	Ruby (-0.8 GB) – A dynamic, object-oriented, general-purpose programming language that is seen as natural to read and overall elegant. SciRuby is the scientist’s collection of tools, similar to Anaconda in many ways. Sources: iruby GitHub
◦	Install dependencies:
▪	sudo apt-get install libtool libffi-dev ruby ruby-dev make git libzmq-dev autoconf pkg-config
▪	cd ~/Codes/src
▪	git clone https://github.com/zeromq/czmq
▪	cd czmq
▪	./autogen.sh && ./configure && sudo make && sudo make install
◦	Install the needed gems and register with jupyter-notebook
▪	sudo gem install cztop iruby
▪	iruby register --user
◦	Install the SciRuby gems:
▪	Gem dependencies (Stack Overflow rmagick install, SciRuby nmatrix GitHub, AskUbuntu GSL-config not found, libzmq GitHub issue): sudo apt-get install libmagickwand-dev imagemagick libatlas-base-dev libgsl-dev libtool-bin
▪	Installation notes that these should be installed first: sudo gem install narray nmatrix
▪	Install the rest: sudo gem install sciruby-full
•	Perl (~0.3 GB) – High-level, general purpose, interpreted, dynamic programming languages that has been used for data mining, system administration, security, and so forth. It can drive a lot of other codes, and is referred to as the “swiss army chainsaw” of programming languages because of its usefulness and ugliness. Sources: p6-jupyter-kernel GitHub for kernel and Rakudo Perl 6, Stack Overflow on configuring Rakudo for installing Perl 6.
◦	Get prereqs: sudo apt-get install build-essential git libssl-dev
◦	Download code and compile:
▪	cd ~/Codes
▪	mkdir rakudo && cd rakudo
▪	curl -LJO https://rakudo.org/latest/star/source
▪	tar -xvzf rakudo-star-*.tar.gz
▪	Rename it to src, and delete the tar file:
•	rm rakudo-star-*.tar.gz
•	mv ./rakudo-star-* ./src
▪	cd src
▪	perl Configure.pl --backend=moar --gen-moar --prefix=/home/jordan/Codes/rakudo/build
▪	make
◦	Run tests if you want:
▪	make rakudo-test
▪	make rakudo-spectest
◦	Install: make install
▪	Add to PATH: nano ~/.bashrc
# Put Rakudo PERL6 in Path so we can use it
export RAKUDO_DIR=/home/jordan/Codes/rakudo/build
export PATH=:$RAKUDO_DIR/bin:$RAKUDO_DIR/share/perl6/site/bin:$PATH
▪	Close and restart terminal.
◦	Install kernel:
▪	Prereqs: sudo apt-get install libzmq-dev
▪	Kernel install: zef install Jupyter::Kernel
◦	Create registration file:
▪	jupyter-kernel.p6 --generate-config
▪	jupyter notebook --generate-config
▪	jupyter console --generate-config
•	C (~0 GB) – General purpose, imperative programming language supporting structured programming. Commonly used for microprocessor and hardware-level programming. Source: c-kernel GitHub
◦	pip install jupyter-c-kernel
◦	install_c_kernel --user
•	C++ (~29.1 GB if built, ~1.8 GB if using binaries) - C, but with objects. Very flexible and common language for all kinds of programming. Source: cling GitHub, Cling download page
◦	K, you can install from source, but I would strongly recommend you just install the binary. Building from source requires more than 16 GB of memory, and consumes nearly 30 GB of storage, and takes all day. It’s not worth it, and we will never need to see the source code for it. I will include the instructions for installing from source, but I’ll gray it out.
◦	Download a Cling binary to ~/Codes: https://root.cern.ch/download/cling, and extract it by clicking on it and pulling out the folder.
◦	Rename the folder cling. Skip past all the gray stuff to PATH.
◦	Install prereqs: sudo apt-get install cmake
◦	Get the Cling Packaging Tool:
▪	cd ~/Codes/scr
▪	wget https://raw.githubusercontent.com/root-project/cling/master/tools/packaging/cpt.py
▪	chmod +x cpt.py
▪	./cpt.py --check-requirements && ./cpt.py --create-dev-env Debug --with-workdir=../cling/
◦	2 problems when building. First, I still accidentally had the MOOSE compilers on PATH. I needed to comment those out. Second, the build process requires over 8 GB of RAM, and I only had 4 GB of RAM with 4 GB of swap, and I maxed out. When I ran this on a systm with more memory (8 GB RAM and 8 GB swap), it peaked at 15 GB of memory use. If you open the cpt.py and search for -j, you’ll find a line similar to the following:
exec_subprocess_call('make -j%d %s %s' % (self.cores, targets, flags),
                                 LLVM_OBJ_ROOT)
If you look a little above that, you’ll see lines similar to the following (line 440 at the time I wrote this):
self.cores = 4
# Travis CI, GCC crashes if more than 4 cores used.
if os.environ.get('TRAVIS_OS_NAME', None):
    self.cores = min(self.cores, 4)
I just set self.cores=1, and commented out the other two lines to make sure that I stayed at 1 core. This then built the rest of the project, though it took all night. I had to force it to stop after it was sitting at 100% building the last object for over 5 hours, and when I ran again, it installed everything and ran some tests using all 4 cores. Success!
▪	Add the following to bashrc: nano ~/.bashrc
# Put Cling in Path so we can use C++ via Cling kernel
export PATH=$PATH:/home/jordan/Codes/cling/bin
◦	Close the terminal, open it again, and install the kernelspec:
▪	cd ~/Codes/cling/share/cling/Jupyter/kernel
▪	pip install -e .
▪	jupyter-kernelspec install --user cling-cpp[ver], replacing [ver] with any of the following values to choose your C++ version:
•	17
•	1z
•	14
•	11
◦	Now, note that cling is running C++ like it’s interpreted. You can’t define int main() at the beginning like you normally would, because Cling already has an int main(). For example, your hello world code would look like this:
#include <stdio.h>
◦	printf("Hello World!\n")
•	Julia (~2.5 GB) – Julia is a general-purpose, multi-talented language that can be used in scientific computing. Source: iJulia GitHub
◦	Install Julia
▪	Download newest full version here. This version is tricked out with lots of goodies and powerful tools for scientific computing and machine learning, among other things (including our Jupyter kernel). You need to create a full account and “buy” the professional license (it’s free). You just need to download the main version (.sh file); you don’t need the ASC or the MKL version (the MKL version uses intel math kernel, so its faster, but we’re on emulated processors, so I don’t think it matters).
▪	Install prereqs: sudo apt-get install curl libzmq5 hdf5-tools libgconf-2-4 default-jdk
▪	Make Java visible to install script: export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-amd64
▪	bash ~/Downloads/JuliaPro-[version]_build-[num].sh /home/jordan/Codes/
▪	Add to our PATH. We need to catch Juno (the IDE), which is in JULIA_PATH, while the Julia executable is deeper in: nano ~/.bashrc
# Add Julia to path
export JULIA_PATH=/home/jordan/Codes/JuliaPro-0.6.2.2
export PATH=$PATH:$JULIA_PATH:$JULIA_PATH/Julia/bin
•	Fortran (~0.5 GB) – A general-purpose, imperative programming language that is especially suited to numeric computation and scientific computing. Many solvers still use FORTRAN today (MOOSE is an example). Sources: CAF kernel GitHub, AskUbuntu on installing gfortran-7,
◦	sudo add-apt-repository ppa:ubuntu-toolchain-r/test
◦	sudo apt-get update
◦	sudo apt-get install gcc-7 g++-7 gfortran-7 cmake
▪	Note: these are installed as gcc-7, g++-c, and gfortran-7 in /usr/bin.
◦	Download and install Coarrays (OpenCoarrays Github):
▪	cd ~/Codes/src
▪	git clone https://github.com/sourceryinstitute/OpenCoarrays.git
▪	cd OpenCoarrays
▪	Install, telling it where our compilers are, and let it download everything else: bash install.sh --with-fortran "/usr/bin/gfortran-7" --with-cxx "/usr/bin/g++-7" --with-c "/usr/bin/gcc-7" --num-threads 4 --install-prefix "/home/jordan/Codes/coarrayfortran"
▪	Allow it to download everything it needs and compile it. It tells us:
# Execute this script via the following command:                                
# source /home/jordan/Codes/coarrayfortran/setup.sh                                             
                                                                                
# Prepend the CMake path to the PATH environment variable:
# Prepend the compiler path to the PATH environment variable:
# Prepend the compiler library paths to the LD_LIBRARY_PATH environment variable:
# Prepend the MPI path to the PATH environment variable:
# Prepend the OpenCoarrays path to the PATH environment variable:
*** To set up your environment for using caf and cafrun, please source the installed setup.sh file in a bash shell or source setup.csh in a C-shell or add one of the following statements to your login file:                                           ***

 source /home/jordan/Codes/coarrayfortran/setup.sh
 source /home/jordan/Codes/coarrayfortran/setup.csh
◦	So, do that. Cmake is taken care of, compilers are taken care of, compiler libraries may be an issue, MPI and OpenCoarrays need to be on path: nano ~/.bashrc
# Adding OpenCoarrays to PATH so that Jupyter can use FORTRAN
export COARRAY_DIR=/home/jordan/Codes/coarrayfortran
export PATH=$PATH:$COARRAY_DIR/bin
export PATH=/home/jordan/Codes/src/OpenCoarrays/prerequisites/installations/mpich/3.2/bin:$PATH
source /home/jordan/Codes/coarrayfortran/setup.sh
◦	Install kernel
▪	cd ~/Codes/src
▪	git clone https://github.com/sourceryinstitute/jupyter-CAF-kernel
▪	cd jupyter-CAF-kernel
▪	pip install -e prebuild/jupyter-caf-kernel
▪	jupyter-kernelspec install prebuild/jupyter-caf-kernel/Coarray-Fortran --user
▪	For some reason, pip had broken, and was giving me the following:
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main,
▪	When I wrote source activate base, pip worked fine.
◦	Start Fortran scripts with the magic “%num_images: 1” (without quotes) to get only one set of output from the code. Multiple start for various reasons (souce: Jupyter-CAF-kernel GitHub).
•	Haskell (~4.2 GB) – general-purpose, purely functional programing with strong static typing. Useful for cryptocurrency contract writing (impossible to run illogical code), and overall very interesting. Sources: IHaskell GitHub, CommercialHaskell GitHub (more info), Haskell Stack Docs
◦	Get prereqs: sudo apt-get install libtinfo-dev libzmq3-dev libcairo2-dev libpango1.0-dev libmagic-dev libblas-dev liblapack-dev
◦	Install Haskell:
▪	cd ~/Codes/src
▪	curl -sSL https://get.haskellstack.org/ | sh
◦	Install IHaskell kernel (without nix—try it out)
▪	git clone https://github.com/gibiansky/IHaskell
▪	cd IHaskell
▪	pip install -r requirements.txt
▪	stack install gtk2hs-buildtools
▪	stack install --fast
▪	ihaskell install --stack
◦	Install IHaskell (with nix)
▪	Install the nix package manager: curl https://nixos.org/nix/install | sh
▪	bash /home/jordan/.nix-profile/etc/profile.d/nix.sh
◦	If install fails, run stack install --fast a few times, as each time it will build different packages. Using this method, I got down to just 4 broken packages left to compile. Then, comment out the problem packages:
▪	go to ~/Codes/src/IHaskell and open stack.yaml, generated during the pip install -r requirements.txt and stack install gtk2hs-buildtools commands. Comment out the problem lines (# is a comment in YAML). For cairo, those problem packages were ./ihaskell-display/ihaskell-charts and ./ihaskell-display/ihaskell-diagrams
▪	When you again run stack install --fast, it will finish the build.
◦	If ihaskell install ---stack fails, try the previous suggestions to get the newest versions on the packages, then try to install it again. For me, libtinfow.so.6 was missing. The package ncurses had it (source).
▪	conda install ncurses=6.1
◦	Add to PATH: nano ~/.bashrc
# A good comment
bash /home/jordan/.nix-profile/etc/profile.d/nix.sh
•	Lisp (~0.1 GB) – sources: cl-jupyter GitHub, Lisp-Lang.org, Quicklisp.org, Quicklisp faq. NOTE: you can also just install beakerx below and you’ll get a version of lisp. This particular kernel is common lisp.
◦	Get prereqs: sudo apt-get install sbcl libzmq3-dev
◦	Get quicklisp:
▪	cd ~/Codes/src
▪	curl -O https://beta.quicklisp.org/quicklisp.lisp
▪	curl -O https://beta.quicklisp.org/quicklisp.lisp.asc
▪	gpg --verify quicklisp.lisp.asc quicklisp.lisp
◦	Fire up a quicklisp terminal, and get lisping:
▪	sbcl --load quicklisp.lisp
▪	(quicklisp-quickstart:install :path "~/Codes/quicklisp/")
▪	(ql:add-to-init-file)
▪	(quit)
◦	Get the kernel:
▪	cd ~/Codes/src
▪	git clone https://github.com/fredokun/cl-jupyter
▪	cd cl-jupyter
▪	source activate base
▪	python ./install-cl-jupyter.py
◦	Install the dependencies in lisp
▪	sbcl --load ./cl-jupyter.lisp
•	BeakerX (~0.6 GB) – This last install includes Groovy, Scala, Clojure, Kotlin, Java, and SQL kernels, all of which include many magics. All these tools run inside of a Java framework, making this the Java kernel, but which also has some neat tools for engineering. This is a good finishing kernel set, as we want Java and SQL, and maybe somebody will find use for the others. Source: beakerx.com
◦	First, what are these languages?
▪	Clojure: a flavor of Lisp with powerful macros. With this, we can forgo the installation of common lisp above.
▪	Groovy: a Java-syntax-compatible object-oriented programming language for the Java platform that can be used as both a programming language and a scripting language and interoperates seamlessly with other Java code and libraries.
▪	Java: this is...well, Java. Java can be run here as interpreted code, so you just start typing your code and can ignore all the class definitions and stuff.
▪	Kotlin: a statically typed programming language that runs on the Java virtual machine and also can be compiled to JavaScript source code or use the LLVM compiler infrastructure.
▪	SQL: a powerful database script that can create and organize a database, manipulate data, and so forth.
▪	Scala: appears to be a better version of Java. It allows many of the same programming techniques, but was created to address the problems that came up in Java.
◦	Change to base install of Python: source activate base
◦	Add via conda-forge: conda install -c conda-forge ipywidgets beakerx

Now that we have all those languages, let’s grab some programming environments for them. Below are the software tools for writing in each of the kernels above. First, the ones that work for most or all of them:
•	Jupyter notebook (~0.1 GB) – this powerful tool was installed above, and we just worked to put all these languages into it as kernels. To run it, type jupyter notebook in a terminal. Wherever your current directory is, that will be your home directory in Notebook. I suggest having a dedicated directory, like ~/Workspace. Keeps things more organized.
◦	After you have started up notebook, you can pick any of the kernels and start going. I added a few things to notebook to make it more usable, though, so I’ll discuss those here.
◦	Setting up a password instead of token (~0 GB). You can use a password for jupyter instead of a randomly generated token. So far, the token is nicer because it just logs you in when you run jupyter notebook, but with the password it asks for it, adding one more step.
▪	After opening notebook, click the Logout button in the top right corner. This takes you to a login page.
▪	Copy the token from the terminal and paste it into the Token box. Then set your password.
▪	After, you log in via your password (in this case, the password is jupyter).
◦	Installing an extension manager (~0.1 GB) (source: jupyter-contrib-nbextensions docs)
▪	Switch to base python: source activate base
▪	Install the extension manager. Doing it through conda will pre-configure a lot of extra tools over the pip install path: conda install -c conda-forge jupyter_contrib_nbextensions
▪	Now you have a nbextensions tab in your jupyter notebook tree, from which you can add extra tools (like code folding) to make your life easier. When you click on one, scroll down to see the explanation of what the extension is and what it does. Check it, and it will be installed.
•	Text editor (gedit) (~0 GB) – this built-in text editor has most of the languages already set up for syntax highlighting. It’s missing gnuplot, lisp, Clojure, Groovy, Kotlin, and SageMath (bash, or command line, is called sh, and Sage can be done as python, so not “missing”). We can download .lang definitions for these languages, which are just xml files and take up almost no extra space.
◦	Gnuplot: according to (source: StackOverflow), gedit is ok for Gnuplot editing
◦	lisp: somebody wrote one on GitHub. Download it.
◦	Clojure: somebody wrote one on GitHub. I’d suggest just getting the .lang file, or you can run the install script as suggested on stackoverflow.
◦	Groovy: again, GitHub has one.
◦	Kotlin: turn once again to GitHub.
◦	For all the above, install them with the following, replacing [lang] with the name you gave the language file:
▪	cd <download directory>
▪	sudo cp [lang].lang /usr/share/gtksourceview-3.0/language-specs/
▪	sudo chmod 644 /usr/share/gtksourceview-3.0/language-specs/[lang].lang
◦	After setting up the .langs, restart gedit (called Text Editor in applications). Select View→Highlight Mode. gedit also includes many languages we don’t have (like XML, LaTeX...look through the list).
•	Vim (~0.2 GB) – a highly popular and old text editor that can be used stand-alone in the command line or as its own GUI. This particular version knows pretty much every language under the sun, and its rather powerful. Source: spf13’s website.
◦	Get prerec (vim): sudo apt-get install vim vim-gnome
◦	Download and install the super distro: curl http://j.mp/spf13-vim3 -L -o - | sh
◦	run vim in command line with vim, and the gui with gvim
◦	to see all the languages it knows, type :setfiletype (with the space), then hit Ctrl+d
◦	From our list, it doesn’t know Octave, Julia, Kotlin, Scala, and SageMath (and SageMath can be viewed as python; Octave as Matlab), and it knows pretty much everything else under the sun.
•	Atom (~0.9 GB) – Atom is another great terminal editor that has some nice features over vim. In particular, it’s GitHub’s own text editor, and can be hacked to do whatever you could possibly hope for. But we need to teach it some languages. Sources include Atom’s online manual, apm GitHub, sitepoint essential atom packages list
◦	To install:
▪	Add Atom’s key: curl -L https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
•	Note: I had it freeze up here. If you run sudo apt-get update first, it’ll ask for sudo password. Then when you do that apt-key add, it’ll be authorized and let you add it. When you pipe it, it seems not to be able to ask for password.
▪	sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
▪	sudo apt-get update
▪	sudo apt-get install atom
◦	Atom has a package manager that comes with it, called Atom apm. We’ll install the IDE-esque package (this is a linter front-end that allows code execution for anything that has an ide language package), then language support, then a few packages to make atom a really powerful IDE.
▪	apm install atom-ide-ui
◦	The easier way to add language support, thought, is in Atom itself.
▪	Open Atom: atom
▪	Edit → Preferences → Install
▪	Search for our different languages. I found the following packages (if it’s not listed, either it’s already installed or wasn’t available):
 
•	ide-bash
•	ide-cpp
•	language-fortran, ide-fortran
•	language-gnuplot-atom
•	language-groovy
•	language-haskell, ide-haskell
•	ide-java
•	language-julia, (ide-julia is still under dev, they have one that connects to Juno, but it’s big and non-trivial to set up)
•	language-kotlin
•	language-lisp
•	ide-python
•	language-matlab (also covers octave)
•	ide-r. (language-r had problems and was no longer maintained)
•	ide-ruby
•	language-sage
•	language-scala
•	scilab-language (This has a lot more features than language-scilab)
 
▪	I also included the following “essential” packages after comparing several Google results:
•	git-plus
•	seti-icons package with monokai theme (nice dark theme)
•	minimap, minimap-highlight-selected (automatically installs dependency highlight-selected)
•	open-recent
•	todo-show
•	Sublime (~0.1 GB) – Sublime is another popular text editor with a bunch of neat features. We’ll install it for completeness. If you use Notepad++ in Windows, Sublime will feel somewhat familiar. Source: Sublimetext.com.
◦	To install:
▪	wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
▪	sudo apt-get install apt-transport-https
▪	echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
▪	sudo apt-get update
▪	sudo apt-get install sublime-text
◦	Open up the package manager by opening sublime text from Applications.
▪	Hit ctr+shift+P, and type packages, select Install Package Control. Alternately, you can go to Tools → Install Package Control.
▪	If you hit ctr+shift+P, type Package Control: you can select discover packages. This takes you to the internet, where you can browse all packages. If you install SublimeLinter, you can get the linter packages (we’ll assume you did that for the langs below). Install them with ctr+shift+P, Package Control: Install Package then,
 
•	SublieLinter-contrib-bashate
•	C++ starting kit, SublimeLinter-clang
•	Enhanced Clojure
•	Fortran
•	Groovy Snippets
•	SublimeHaskell
•	Julia
•	Kotlin
•	Python 3
•	GNU Octave Completions
•	Perl Completions, SublimeLinter-contrib-perl
•	Ruby Completions, SublimeLinter-ruby
•	Scala Syntax
•	Scilab
 
◦	Again, some essential packages:
▪	Git, Gist
▪	Filediffs
▪	BracketHighlighter
▪	SublimeLinter
•	Eclipse (~X.X-37.5 GB) – TODO: you are looking into how many of these languages you can cram into Eclipse.
•	Code::Blocks (~X.X GB) – TODO: haven’t even looked at Code::Blocks yet
•	Visual Studio Code (~X.X GB) – TODO: haven’t even looked at Visual Studio Code yet, but it is installed (via Anaconda).

For each language/environment (listing what tools to use, and how to install any additional IDEs if there were any):
•	Python
◦	Spyder (~X.X GB). It was installed with Anaconda. To run it, just type spyder in a terminal.
▪	I then went to Tools → Preferences → Current working directory, and told it to use ~/Workspace
▪	Then Tools → Pythonpath → Added anaconda’s environments (paths by conda env list)
•	SageMath
◦	The preferred IDE for SageMath is Jupyter notebook. Run it by typing jupyter notebook, and then choose a SageMath kernel.
•	Machine Learning
◦	To be able to program in machine learning, you just need to add it to the PYTHONPATH in spyder, or run it it Jupyter
•	R
◦	RStudio seems to be the go-to. Download: https://www.rstudio.com/products/rstudio/download/#download
◦	Double-click to install.
◦	Run from terminal (rstudio) or run from the Ubuntu logo.
•	Gnuplot
◦	
•	Scilab
•	Octave
•	bash
•	Ruby
•	Perl
•	C
•	C++
•	Fortran
•	Lisp
•	Haskell

RAVEN
Following instructions from https://github.com/idaholab/raven/wiki/installationLinux
•	pre-recs: sudo apt-get install libtool git
•	clone: cd ~/Codes
◦	git clone https://github.com/idaholab/raven.git
◦	cd raven
◦	git submodule init moose
◦	git submodule update moose
•	Set up the RAVEN environment in conda
◦	conda create -m --name raven_libraries -y numpy=1.11.0 h5py=2.6.0 scipy=0.17.1 scikit-learn=0.17.1 matplotlib=1.5.1 python=2.7 hdf5 swig pylint lxml
◦	source activate raven_libraries
•	Compile RAVEN
◦	cd ~/Codes/raven
◦	make
•	Test RAVEN (from ~/Codes/raven): ./run_tests
◦	Tests successful if most are passed (~300-400), several are skipped, and none fail. Skipped ones are for modules that aren’t distributed standard with the code.
•	For me (7 April 2018): 489 passed, 57 skipped, 0 failed.

MOOSE
Following instructions from http://mooseframework.org/wiki/BasicManualInstallation/Linux
•	pre-recs: sudo apt-get install build-essential gfortran tcl git m4 freeglut3 doxygen libblas-dev liblapack-dev libx11-dev libnuma-dev zlib1g-dev libhwloc-dev
•	clone: cd ~/Codes
◦	git clone https://github.com/idaholab/moose.git
◦	cd ~/projects/moose
◦	git checkout master
•	Put the following in bashrc:
◦	nano ~/.bashrc
◦	Paste at the end:
# MOOSE ADDITIONS
# Compiler Variables
export CC=mpicc
export CXX=mpicxx
export F77=mpif77
export FC=mpif90

# Library location
export PACKAGES_DIR=/opt/moose

# Helper variables
export GCC_HOME=$PACKAGES_DIR/gcc_6.2.0
export MPI_HOME=$PACKAGES_DIR/mpich/mpich_3.2
export PETSC_DIR=$PACKAGES_DIR/petsc/mpich_petsc-3.7.6/gcc-opt
export PEACOCK_DIR=/home/jordan/Codes/moose/python/peacock

# PATH
export PATH=$GCC_HOME/bin:$MPI_HOME/bin:$PATH
export PATH=$PATH:$PEACOCK_DIR

# LD_LIBRARY_PATH
export LD_LIBRARY_PATH=$GCC_HOME/lib:$GCC_HOME/lib64:$GCC_HOME/lib/gcc/x86_64-pc-linux-gnu/6.2.0:$GCC_HOME/libexec/gcc/x86_64-pc-linux-gnu/6.2.0:$LD_LIBRARY_PATH

# JOB Count (the number of cores available on this machine)
export MOOSE_JOBS=4
◦	Close all terminals, and re-open then to let this be pulled into your terminal.
•	Update g++ and gcc:
◦	Download the MOOSE gcc tarball from the source above
◦	mkdir ~/Codes/src && cd ~/Codes/src
◦	tar -xf ~/Downloads/gcc-6.2.0.tar.gz -C .
◦	mkdir gcc-build && cd gcc-build
◦	I think the following steps un-links previous compilers, but I don’t know for sure.
◦	unset CC
◦	unset CXX
◦	unset FC
◦	unset F90
◦	unset F77
◦	This sets up the needed stuff to get the build right. It should end with a line saying something like “creating Makefile”
◦	../gcc-6.2.0/configure --prefix=$GCC_HOME --disable-multilib --enable-languages=c,c++,fortran --enable-lto
◦	make
◦	sudo -E make install
•	Download and install an MPI wrapper (following instructions from MOOSE wiki above). After download:
◦	cd ~/Codes/src
◦	tar -xf ~/Downloads/mpich-3.2.tar.gz -C .
◦	mkdir mpich-3.2/gcc-opt && cd mpich-3.2/gcc-opt
◦	This sets up the needed stuff to get the build right. Should end with something like “Configuration complete”
◦	../configure --prefix=$MPI_HOME --enable-shared --enable-sharedlibs=clang --enable-fast=03 \
◦	--enable-debuginfo --enable-totalview --enable-two-level-namespace CC=gcc CXX=g++ FC=gfortran F77=gfortran F90='' CFLAGS='' CXXFLAGS='' FFLAGS='' FCFLAGS='' F90FLAGS='' F77FLAGS=''
◦	make
◦	sudo -E make install
•	Download and install the PETSc solver. Again, download it using the link in the instructions. Then:
◦	cd ~/Codes/src
◦	tar -xf ~/Downloads/petsc-3.7.6.tar.gz -C .
◦	cd petsc-3.7.6
◦	Paste in this whole block. Note, differs from the website because I got the message that python3 doesn’t support configure yet:
◦	python2 './configure' '--prefix=/opt/moose/petsc/mpich_petsc-3.7.6/gcc-opt' '--download-hypre=1' '--with-ssl=0' '--with-debugging=no' '--with-pic=1' '--with-shared-libraries=1' '--with-cc=mpicc' '--with-cxx=mpicxx' '--with-fc=mpif90' '--download-fblaslapack=1' '--download-metis=1' '--download-parmetis=1' '--download-superlu_dist=1' '--download-mumps=1' '--download-scalapack=1' 'CC=mpicc' 'CXX=mpicxx' 'FC=mpif90' 'F77=mpif77' 'F90=mpif90' 'CFLAGS=-fPIC -fopenmp' 'CXXFLAGS=-fPIC -fopenmp' 'FFLAGS=-fPIC -fopenmp' 'FCFLAGS=-fPIC -fopenmp' 'F90FLAGS=-fPIC -fopenmp' 'F77FLAGS=-fPIC -fopenmp' 'PETSC_DIR=/home/jordan/Codes/src/petsc-3.7.6'
◦	My custom make instructions (exactly what to run is printed at the end of the output for the command above): make PETSC_DIR=/home/jordan/Codes/src/petsc-3.7.6 PETSC_ARCH=arch-linux2-c-opt all
◦	My custom make install instructions: sudo make PETSC_DIR=/home/jordan/Codes/src/petsc-3.7.6 PETSC_ARCH=arch-linux2-c-opt install
◦	After, there are custom test instructions. Mine: make PETSC_DIR=/opt/moose/petsc/mpich_petsc-3.7.6/gcc-opt PETSC_ARCH="" test
◦	Then: make PETSC_DIR=/opt/moose/petsc/mpich_petsc-3.7.6/gcc-opt PETSC_ARCH= streams
•	That should be it! Your MOOSE environment should be done! However, the system couldn’t open matplotlib for some reason…
•	Make sure you close your terminal, and re-open it before finishing the installation.
•	Compile libMesh:
◦	cd ~/Codes/moose
◦	scripts/update_and_rebuild_libmesh.sh
•	Finally, you can compile MOOSE itself, and run the tests for it:
◦	cd test
◦	In the Google User Group, they note that the python development libraries are needed for the test file parser, but they hadn’t updated the install instructions. So: sudo apt-get install python-dev
◦	You also need to run MOOSE using Python 2.7: conda create -m -n moose anaconda python=2.7
◦	source activate moose
◦	make
◦	./run_tests
•	For me, 1551 passed, 51 skipped, 0 failed.
•	That’s it! MOOSE is now installed! Make sure to switch to moose environment each time you run it!

Miscellaneous other additions/notes
There are other useful programs and things that I did on this box that I document here.
•	Install Atom: Atom is a very handy terminal editor. ref: https://flight-manual.atom.io/getting-started/sections/installing-atom/
◦	curl -L https://packagecloud.io/AtomEditor/atom/gpgkey | sudo apt-key add -
◦	sudo sh -c 'echo "deb [arch=amd64] https://packagecloud.io/AtomEditor/atom/any/ any main" > /etc/apt/sources.list.d/atom.list'
◦	sudo apt-get update
◦	sudo apt-get install atom
•	Sublime: Sublime is a powerful text editor with neat plugins for LaTeX and other things. https://www.sublimetext.com/docs/3/linux_repositories.html#apt
◦	Install GPG key: wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
◦	Get apt ready to go: sudo apt-get install apt-transport-https
◦	Pick Sublime channel: echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
◦	Update apt and install: sudo apt-get update && sudo apt-get install sublime-text
◦	That’s it! You can run it from the “Start Menu”. You can install plugins by adding the package manager following instructions at https://packagecontrol.io/installation
◦	Then go to Preferences→Package Control, and you can search or install or whatever from there. I have added the LaTeXing package.
•	Mendeley: a fantastic academic source manager
◦	Download the package: https://www.mendeley.com/guides/download-mendeley-desktop/ubuntu/instructions
◦	Install via the instructions there.
◦	Open it, sign in, and then install the plugins. It will ask you to install them when you log in, but should you forget or that message doesn’t appear: Tools → Install Web Importer and Libre Office Source Manager.
◦	This will now update with sudo apt-get update && sudo apt-get upgrade
•	Spyder: powerful python IDE
◦	Open the app store, and find Spyder 3 (you can also get Spyder 2 if you use Python2). Click install. Done!
•	Rstudio: powerful R IDE
◦	Download the package: https://www.rstudio.com/products/rstudio/download/#download
◦	Double-click on the downloaded package, and it will install itself. Yay!
•	VLC
◦	Download from the app store.

The full ~/.bashrc file after following all the install instructions above:
TO COME
