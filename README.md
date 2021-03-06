# BeCorrect
*New in v1.1.0: BeCorrect now accepts decimal values for "counts" table to work with edgeR normalization, quartile normalization, etc.
BeCorrect (v.1.1.0) is distributed as a standalone .cpp file.  BeCorrect can be compiled in either linux or Mac OS X using the following command:

g++ BeCorrect.cpp -o BeCorrect

Usage for BeCorrect can be displayed by running BeCorrect with no parameters supplied:

BeCorrect (v1.1.0): A program to rescale bedgraph files to visually match batch correction using RUVSeq.

  Usage: BeCorrect <raw_counts> <ruv_adjusted_counts> <chr.names> 1.bg ... n.bg

Creates batch corrected bedgraph files based on batch correction performed by RUVseq on counts table for CHIPseq/ATACseq peaks.  For CHIP/ATAC, raw counts, adjusted counts, and bedgraph files should be sorted by chromosome then start location.

Sample counts file for CHIP/ATAC should be as follows:
chr	start	end	name1	...	nameN
Name1	start1	end1	Val1.1	...	ValN.1
Name2	start2	end2	Val1.2	...	ValN.2

A full testing data set is available at http://brc.wustl.edu/SPACE/pgontarz/BeCorrect/BeCorrect_Test_Data.tar.gz.  To use this testing dataset, download and decompress using the command:

tar -xzvf BeCorrect_Test_Data.tar.gz

The decompressed directory contains 11 files: 8 bedgraph (.bg) files, a raw counts file, an adjusted counts file, and a chromosome names file.  From the directory containing the files, these can be used to run BeCorrect with the following command:

BeCorrect Raw_Counts.txt Adjusted_Counts_k3.txt rn6.names.txt 14_AH_raw.bg 15_AH_raw.bg 21_AH_raw.bg 22_AH_raw.bg 14_DG_raw.bg 15_DG_raw.bg 21_DG_raw.bg 22_DG_raw.bg

*Note: The .bg files must be supplied in the same order as the columns in the counts table.  BeCorrect does not check that files are supplied in the correct order.

It has been our experience that for a full-sized bedgraph file on a mammalian genome, BeCorrect requires ~1 min per file.
