#	Makefile corresponding to BAM2HINTS
#	
# 	NOTE:
#	a) "-g" option allows for debugging
#	b) libbamtools.a and lz library are used during the linking process
#
# 	Created: 14-December-2011
#	Last modified:  23-October-2017 by Jon Palmer

# Variable definition
BAMTOOLS=/usr/local/bamtools
INCLUDES = $(BAMTOOLS)/include
LIBS = $(BAMTOOLS)/lib/libbamtools.a -lz
SOURCES = bam2hints.cc 
OBJECTS = $(SOURCES:.cc=.o)
CFLAGS = -Wall -O0 -g -ggdb # -g -p

# Recipe(s)
# $@: full target name of current target. 
# $<: .c file of target. 
bam2hints : $(OBJECTS) 
	$(CXX) $(CFLAGS) -o $@ $(OBJECTS) $(LIBS) 
	cp bam2hints ../../bin

all:$(OBJECTS) # Compiles each foo.cc into foo.o

bam2hints.o : $(SOURCES)
	$(CXX) $(CFLAGS) -c $< -o $@ -I$(INCLUDES) 

clean: 
	rm -f bam2hints.o bam2hints ../../bin/bam2hints
