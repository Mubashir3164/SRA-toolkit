# SRA-toolkit (Using SRA to download and process sequencing data from NCBI database)
What SRA-toolkit is for?
It is a set of utilities to download and process sequencing data from NCBI at large scale. NCBI SRA (Sequence Read Archive) database contains sequenced data in SRA format. SRA is a primary repository for high-throughput sequencing data hosted by NIH. The SRA is also a member of the International Nucleotide Sequence Database Collaboration (INSDC), which also includes the European Bioinformatics Institute (EBI) and the DNA Database of Japan (DDBJ).
SRA data can be downloaded using run accessions (SRR Ids).

Download the latest version of SRA toolkit (verion 3.0.0)

# run the following command to download
wget https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.0/sratoolkit.3.0.0-ubuntu64.tar.gz
# Extract the tar.gz file 
tar -zxvf sratoolkit.3.0.0-ubuntu64.tar.gz
# Export the sratoolkit binaries to path
export PATH=$PATH:/home/Abbas/tools/sratoolkit.3.0.0-ubuntu64/bin
# Next step is configure SRA toolkit

Few options must be enabled to access public cloud data from SRA, to perform this task run ghe following command

vdb-config -i

after running this command an interface will appear that ask you to press a letter highlighted in red or to use either the tab key to navigate to a desired button and then press either space or enter. Open the below link to know in detail about SRA toolkit configuration. 
https://github.com/ncbi/sra-tools/wiki/03.-Quick-Toolkit-Configuration

Next step is to Download sequencing datasets from SRA database

# for single SRA file
Prefetch SRR19850882 
# for multiple files
Prefetch SRR19850882 SRR19850883 SRR19850884

note: a text file containing SRR numbers can also be provided to download multiple sra files, or SraAccList.txt can be directly download from SRA using 'Send to' dropdown menu to download all SRA hits of your desired sequencing project. 
# After downloading SRA files convert it to fastq format by using fastq-dump or fasterq-dump

fastq-dump SRR19850882 SRR19850883 SRR19850884 # provide single or multiple files 

fastq-dump can replaced with fasterq-dump which is more faster

fasterq-dump SRR19850882 SRR19850883 
# Note: for reads generated by paired end sequencing  use --split-files option with fastq-dump
 fastq-dump --split-files SRR19850882 SRR19850883 SRR19850884
# data can also be downloaded in FASTQ format direclty without using prefetch, but it will be slower.
 NOTE for parallel-fastq-dump visit the below link
 https://github.com/rvalieris/parallel-fastq-dump

