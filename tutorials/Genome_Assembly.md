# Running velveth
[For Simple understanding how velevt assemble works Read this](https://en.wikipedia.org/wiki/Velvet_assembler)

- Typical velveth command 
```
# Just type 
veleveth
# ./velveth directory hash_length {[-file_format][-read_type][-separate|-interleaved] filename1 [filename2 ...]} {...} [options]
```
### Little discription about command option
- directory --> Where should store the output files
- hash_length --> What kmer size do you want ( choose *odd* number)
- file_format --> What is format of data ( fasta,fastq,sam,bam,zipped,raw)
- read_type --> Is it short, long any other type
- separate --> If you have paired end read data they are present in two separate files filename1, filename2
- interleaved --> If you have paired read data they are present in single files

```
velveth Assem_31 31 -shortPaired -fasta interleaved.fna  # For the data having reads in single file

velveth Assem_31 31 -shortPaired -fastq -separate left.fq.gz right.fq.gz # For the data having reads in two differnet files

velveth Assem_29 29 -short -fastq s_1_sequence.txt # For the short-single end reads
```
Above command tells that create a directory named as Assem_31 for the kmer-size of 31 using fastaq reads which are shortPaired(~100-150bp) present in two separate files.

### Output
**You will get two different file in the output directory (Assem_31)**
- Roadmaps
- Sequences

# Running velvetg
In the above steps we have created files needed as input for velvetg (Assem_31), we will be using this for next step.

- Typical velveth command 
```
#Just type
velvetg 

#./velvetg directory [options]
```

### Little discription about command option
- directory --> It is asking path of directory that we was created by velveth

```
velvetg Assem_31
```
### Output
- contigs.fa --> fasta file of contigs longer than twice hash length
- stats.txt	-->  stats file (tab-spaced) useful for determining appropriate coverage cutoff
- LastGraph	--> special formatted file with all the information on the final graph

# Getting Assembly stat
- Using assembly_metric.sh (Shell)
- using assembly_stats (python)
- using assemblathon_stats.pl (perl)
