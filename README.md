# augustus
AUGUSTUS v3.2.1 for installation on Mac OS X

AUGUSTUS v3.2.1 was downloaded from http://bioinf.uni-greifswald.de/augustus/binaries/old/augustus-3.2.1.tar.gz. And the Makefiles were subsequently modifed so that it could compile and be functional on Mac OSX.  The problem seems to be something in the ProteinProfile function, where if compiled with Mac `clang++` it will throw an error everytime you try to use the proteinprofile method - thus Augustus won't work with BUSCO.  The workaround is to use `g++` v4.8 or greater, I install gcc using homebrew which will currently get you `gcc-7`, you can install with `brew install gcc`.

The other major source of pain in this install is linking Bamtools correctly to the accessory scripts/programs in the `auxprogs` folder.  The important point here seems to be (at least this is the only way I could get it to work) is to make sure that the same compiler that you build Bamtools v2.4.0 with, is also what you use to compile these accessory programs.  To make this work, I added two variables to the make command to make sure you are aware of this and are specifiying the correct compiler.

So in order to install from here you should do the following:
```
#first install Bamtools, compile with native Apple Clang compiler
wget https://github.com/pezmaster31/bamtools/archive/v2.4.0.tar.gz
tar -xzvf v2.4.0.tar.gz
cd bamtools-2.4.0

#now to make Cmake use Apple (in case you have other compilers which you might)
export CC=clang
export CXX=clang++

#now build bamtools
mkdir build
cd build
cmake ..
make
```
At this point you should have a working version of bamtools v2.4.0, double check that inside the bamtools folder you now see a `bin`, `lib`, and `include` folders. Now clone this repository and build Augustus. Of course you need to specify the location of where you compiled bamtools to the BAMTOOLS variable.
```
git clone https://github.com/nextgenusfs/augustus.git
cd augustus

#now build with 
make CC=gcc-7 CXX=g++-7 BAMTOOLS_CC=clang BAMTOOLS_CXX=clang++ BAMTOOLS=/path/to/bamtools

#you should get a few warnings, but after it builds you can install
sudo make install
```
By default Augustus will install to `/opt/augustus-3.2.1/`, not you can change this during the `make install` command.  You have one last thing to do, make sure Augustus and ENV variables are in path.
```
export PATH=/opt/augustus-3.2.1/bin:$PATH
export AUGUSTUS_CONFIG_PATH=/opt/augustus-3.2.1/config
```
