# FR-HIT

Fr-hit is a fast program to recruit the metagenomic reads to reference genomes. In the metagenomic data analysis, fragment recruiment is a important process of aligning the reads to the reference genome


# Installation instructions for FR-HIT:

git clone https://github.com/Beifang/fr-hit.git

cd fr-hit

sudo mv fr-hit /usr/local/bin/

make

# Usage: fr-hit v0.7 [options]


    -a   <string>   reads file, *.fasta format
    -d   <string>   reference genome sequences file, *.fasta format
    -o   <string>   output recruitments file
    -e   <double>   e-value cutoff, default=10
    -u   <int>      mask out repeats as lower cased sequence to prevent spurious hits? 1: yes; 0: no; default=1
    -f   <int>      format control for output file,0:FR-HIT format; 1:PSL fromat, default=0
    -k   <int>      k-mer size (8<=k<=12), default=11
    -p   <int>      k-mer overlap of index (1<=p<-k), using small overlap for longer reads(454, Sanger), default=8
    -c   <int>      sequence identity threshold(%), default=75
    -g   <int>      use global or local alignment? 1:global; 0:local (need -m), default=0
    -w   <int>      minimal read length to use 2bp k-mer index step to 454 long reads, default=1000
    -m   <int>      minimal alignment coverage control for the read (g=0), default=30
    -l   <int>      length of throw_away_reads, default=20
    -t   <int>      maximum number of failed alingment attempts, default=20
    -r   [0,N]      how to report alignment hits, 0:all; N:the best top N hits for one read, default=0
    -n   <int>      do alignment for which chain? 0:both; 1:direct only; 2:complementary only. default=0
    -b   <int>      band_width of alignment, default=4
    -T   [0,N]      number of threads, default 1; with 0, all CPUs will be used
    -h   help
    
Example:

sudo ./fr-hit -a SRR072233.fasta -d Acinetobacter_baumannii_genomic_RefSeq.fasta -c 75 -m 40 -w 120 -r 0 -o
Acinetobacter_baumannii.sop

In this analysis, I used SRR07233.fasta dataset to reference genome; Acinetobacter_baumannii_genomic_RefSeq.fasta.The setting I used for FR-HIT is -d = reference genomes in fasta format
which I have. -o for output file, -a = input file I fasta format. -c =90 I kept percent identity threshold default at
75, -w= 30 which is minimal read length, and -r = 0 which is 0: all( report all alignment). The output file format
is sop.

