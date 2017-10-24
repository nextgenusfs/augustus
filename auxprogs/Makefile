# Makefile for auxprogs
#
# Created on: 16-October-2016
# Last modified on: 16-October-2016 by Katharina Hoff (katharina.hoff@gmail.com)

all:
	cd bam2hints; make CXX=$(BAMTOOLS_CXX) CC=$(BAMTOOLS_CC) BAMTOOLS=$(BAMTOOLS);
	cd compileSpliceCands; make CXX=$(BAMTOOLS_CXX) CC=$(BAMTOOLS_CC);
	cd filterBam; make CXX=$(BAMTOOLS_CXX) CC=$(BAMTOOLS_CC) BAMTOOLS=$(BAMTOOLS);
	cd homGeneMapping; make CXX=$(BAMTOOLS_CXX) CC=$(BAMTOOLS_CC);
	cd joingenes; make CXX=$(BAMTOOLS_CXX) CC=$(BAMTOOLS_CC);
clean:
	cd bam2hints; make clean;
	cd compileSpliceCands; make clean;
	cd filterBam; make clean;
	cd homGeneMapping; make clean;
	cd joingenes; make clean;
