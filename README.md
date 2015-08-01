# MeFiT

##############################################################################
Program : MeFiT (Merging and Filtering Tool for Paired-End Reads)

Description : This pipeline will merge overlapping paired-end reads, calculate 
              merge statistics, and filter reads for quality


Author : Hardik I. Parikh, PhD (parikhhi@vcu.edu)

Date : Jan 20, 2015

Version : v1.0

Contact : Nihar U. Sheth (nsheth@vcu.edu)
##############################################################################


# Prerequisites:


Python version 2.7 (version 3.0 or greater may not work)


Python modules
 
numpy 	installation instructions:	http://www.numpy.org/

HTSeq 	installation instructions:	http://www-huber.embl.de/users/anders/HTSeq/doc/install.html
	

CASPER (Context-Aware Scheme for Paired-End Read)

installation instructions:	http://best.snu.ac.kr/casper


Jellyfish mer counter

installation instructions:	http://www.genome.umd.edu/jellyfish.html



# Usage : 
	$mefit -s sampleID -r1 R1.fastq -r2 R2.fastq [OPTIONS]


	[REQUIRED ARGUMENTS]

	-s	<str>		Sample name	sampleID

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

	-nonovlp		Merge the non-overlapping reads 
					Default: False		

	-n	<int>		Length of Ns to insert between non-overlapping reads for merging
					Default: 15

	-avgq	<int>		AvgQ threshold for Quality Filtering
	OR
	
	-meep	<float>		meep score threshold for Quality Filtering


# Example :

	$mefit -s sample -r1 sample_R1.fastq -r2 sample_R2.fastq -avgq 20

	$mefit -s sample -r1 sample_R1.fastq -r2 sample_R2.fastq -meep 1.0

	$mefit -s sample -r1 sample_R1.fastq -r2 sample_R2.fastq -p casper.params -nonovlp -n 15 -avgq 20

	$mefit -s sample -r1 sample_R1.fastq -r2 sample_R2.fastq -p casper.params -nonovlp -n 15 -meep 1.0

	
	CASPER Output Files :
	
	sample.fastq			Merged reads
	sample_for_left.fastq		Non-overlapping forward reads
	sample_rev_left.fastq		Non-overlapping reverse reads
	sample.casper.log		CASPER log file
	

	MeFiT Output Files :

	sample.ovlp.fastq		Merged overlapping reads
	sample.ovlp.hq.fastq		Merged overlapping High-Quality reads
	sample.nonovlp.fastq		Merged Non-overlapping reads
	sample.nonovlp.hq.fastq		Merged Non-overlapping High-Quality reads
	sample.stats.txt		Sample Statistics Report
	mefit_params.txt		Log of MeFiT parameters

##############################################################################
