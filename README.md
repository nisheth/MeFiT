# MeFiT

##############################################################################
Program : MeFiT (Merging and Filtering Tool for Paired-End Reads)

Description : This pipeline will merge overlapping paired-end reads using 
	      CASPER, calculate merge statistics, and filter reads for quality
	      using the maximum exprected error based on read length (that is,  
	      a 1% error in a read of length 500 means a MEE threshold of 5).


Author : Hardik I. Parikh, PhD (parikhhi@mymail.vcu.edu)

Date : Jan 20, 2015

Version : v1.0

Contact : Nihar U. Sheth (nsheth@vcu.edu)
##############################################################################


Prerequisites:

Python version 2.7 (version 3.0 or greater may not work)
Python module 
\n	numpy 	installation instructions:	http://www.numpy.org/
\n	HTSeq 	installation instructions:	http://www-huber.embl.de/users/anders/HTSeq/doc/install.html
	
CASPER (Context-Aware Scheme for Paired-End Read)
		installation instructions:	http://best.snu.ac.kr/casper

Jellyfish mer counter	
		installation instructions:	http://www.genome.umd.edu/jellyfish.html



Usage : mefit -r1 R1.fastq -r2 R2.fastq [OPTIONS]


	[REQUIRED ARGUMENTS]

	-r1	<str>		Forward read	R1.fastq

	-r2	<str>		Reverse read	R2.fastq 



	[OPTIONS]

	-p	<str>		CASPER parameters file (tab-delimited) 
					Default:    casper.params
						threads : 12
						k-mer length : 17
						threshold for difference of quality-score : 20
						threshold for mismatch-ratio : 0.2
						minimum overlap length : 15

	-e	<float>		Percent error cut-off - MEE threshold value
					Default: 1.0

	-a			Merge all reads, including the non-overlapping reads 
					Default: False		

	-n	<int>		Length of Ns to insert between non-overlapping reads for merging
					Default: 15

##############################################################################

