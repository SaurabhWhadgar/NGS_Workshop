## Variant calling pipeline

> **NOTE**: Use nohup command if you need to run the process in background (No worry of loose internet connection) which stands for no hangup. nohup ensuers that commands runs in background even if you exit the shell or terminal. 

> To know the status of you process/jobs that you have submitted use 'jobs' command, type it in terminal.
>> `jobs`

### 1. Getting a SAM file
```
nohup bowtie2 -x indexed_ref_file -1 Read1_file.fq -2 Read2_file.fq -S sample.sam &
```
- -x takes indexed reference file as input. 
- -1 and -2 is for paired end data. -1 takes read1 file and -2 takes read2 file in fastq format as input.
- -S is to get a SAM file as output. After aligning reads with reference, we get a SAM file and that will be our alignment file. 

### 2. Converting sam file to bam file
``` 
samtools view -S -b sample.sam > sample.bam
```
### Explanation
- -S stands for input SAM file and -b stands for getting a BAM file output.
- .sam file is  a user readable file while .bam file is the binary format of sam file for computer recognition.
- .bam file takes quite less storage space and is faster to manipulates as compared to .sam file because it is the binary or compressed version of file.sam.

To see the memory space difference between SAM file and BAM file:

```
ls -lh
```
### 3. Convert bam to sorted bam
```
samtools sort file_name.bam -o sorted_file.bam.
```
### Explanation
- We sort the BAM file to keep the reads/contigs in order of genome or chromosome.
- Sorting BAM file arranges reads in order and makes easy for next tools to work properly . 
- BAM file gets sorted based on starting and end position of reads/contigs in the genome.

### 4. Index the sorted bam file
```
samtools index file.sorted.bam 
```

### Explanation
- **Indexing** a sorted **BAM** file allow us to quickly extract alignments that overlaps to the particular region of the reference genome.
- Output indexed sorted BAM file will be in BAM.bai format.
- **NOTE**: The indexed BAM file and the sorted BAM file have to be in the same directory to proceed further.

### 5. Indexing the reference fasta file
```
samtools faidx reference_file.fasta
```

### Explanation
- **Indexing** **reference.fasta** file help the easy access to any random base in the reference genome sequence.
- Output file will have the same name as that of the input file with an extention of .fai (reference.fasta.fai)
### 6. mpileup to get a VCF (Variant Calling Format) file
```
vcftools mpileup -f reference.fasta -o output_file.vcf sorted_bam_file.bam
```
### Explanation
- -f reference fasta file
- -o name of output vcf file
- sorted BAM file as in input

### To see output.vcf file
```
less output.vcf
```

### Explanation
- The line starts with '#' are important because it contains the informatation related the vcf file. 
- Different coloumns in the files have their own meanings e.g 1st columns have chromosome number, secound column have chromosome id e.t.c.
- The column REF and ALT are important to notice. The bases given in the REF denotes the nucleotide base present in that chromosome at that perticular position. '*' in ALT shows that alternate (read) have same base at that position. If REF have a 'A' and ALT have 'G' that means there is an 'A' in reference genome while 'G' in the read. If there is an 'A' in REF and and G, star in ALT then it means there might be a sequencing error (false positive) or equal posibility of having A or G.
#### ***Example:***
| REF      | ALT     |MEANING  |
| ---------| --------|---------|
| CAAAAAA  | CAAAAA  |deletion |
| CAAAAA   | CAAAAAA |insertion|
| A        | G,<*>   |can be false positive case
| A        | *  | same as reference

### 7. Calling variant
```
bcstools -vmO -o output_call.vcf input_file.vcf
```

### Explanation
- -v stands for output file will be in uncompressed vcf format.
- m will include multiallelic results too i.e. it will also include the result if multiple bases have same probability to present at that perticular position. 
- -O stands for output file type.
