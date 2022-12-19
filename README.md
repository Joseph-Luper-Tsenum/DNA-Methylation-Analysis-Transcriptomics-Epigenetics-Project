# CpG Methylation in Early Mouse Embryonic Development WGBS Samples - (Sequencing of the Whole Bisulfite Genome)

### By Joseph Luper Tsenum

Email: tsenumjosephluper@phystech.edu

Phystech School of Biological and Medical Physics (FBMF)

Moscow Institute of Physics and Technology (National Research University)

Russian Federation

### Introduction

Chromosome Used: Chromosome 19 of Genome mm10 was used for alignment. FastQC Reports for the three samples is contained in the uploaded pdf file.

### Bismark Report

Bismark statistics can be found in the uploaded pdf file while the plots can be found below:

                  Before Bismark Methylation extraction is shown below 
![image](https://user-images.githubusercontent.com/58364462/208530346-f5114e8a-f544-43fe-9594-396ca5d091d8.png) 


                  After Bismark Methylation Extraction in Epiblast Rep1 is shown below 
![image](https://user-images.githubusercontent.com/58364462/208530413-4b8a545c-23e6-4f1d-97c8-39c67fcf0022.png)


                  ICM Rep 2 M-Bias plot is shown below 
![image](https://user-images.githubusercontent.com/58364462/208530946-58f515a4-95c0-4fcd-9d72-699dd936c46b.png)




### The Histograms below shows the CpG Cytosine Methylation Levels Generated Using R package

                  Average methylation level for Epiblast_rep1 = 0.7588857 as shown below 
![image](https://user-images.githubusercontent.com/58364462/208531037-43ff4bca-e150-48c4-84e7-7023c2c0d340.png)


                  Average methylation level for Epiblast_rep2 = 0.7588857 as shown below 
![image](https://user-images.githubusercontent.com/58364462/208531202-4e5dbafd-c372-4907-9b19-53a96de12643.png)


                  Average methylation level for ICM_rep2 = 0.1711466 as shown below 
![image](https://user-images.githubusercontent.com/58364462/208531766-fe7d31d3-2647-4e15-b371-e0fbc38c4dab.png)

![image](https://user-images.githubusercontent.com/58364462/208531827-1ce61df4-40d8-4bcc-ade5-dde2696bf0a0.png)


### Commands Used

Running fastq
```bash
fastq 8cell_rep1_trimmed_WGBS_R1.fastq.gz 8cell_rep1_trimmed_WGBS_R2.fastq.gz
8cell_rep2_trimmed_WGBS_R1.fastq.gz 8cell_rep2_trimmed_WGBS_R2.fastq.gz
Epiblast_rep1_trimmed_WGBS_R1.fastq.gz Epiblast_rep1_trimmed_WGBS_R2.fastq.gz
Epiblast_rep2_trimmed_WGBS_R1.fastq.gz
Epiblast_rep2_trimmed_WGBS_R2.fastq.gzICM_rep1_trimmed_WGBS_R1.fastq.gz
ICM_rep1_trimmed_WGBS_R2.fastq.gz ICM_rep2_trimmed_WGBS_R1.fastq.gz
ICM_rep2_trimmed_WGBS_R2.fastq.gz
```

Bismark Genome Preparation
```bash
to-mr -v -m bismark -o Epiblast_rep1_WGBS_1.deduplicated.mr
Epiblast_rep1_WGBS_1.deduplicated.bam
```

Sorting 
```bash
sort -k 1,1 -k 2,2n -k 3,3n -k 6,6 -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.mr
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.mr
```
Alignment to chr19
```bash
methpipe/methpipe-3.4.3/bin/analysis/methcounts -cpg-only -c mouse_chr/chr19.fa -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated
```
Getting mr
```bash
methpipe/methpipe-3.4.3/src/analysis/methcounts -cpg-only -c mouse_chr/chr19.fa -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.mr
```

Getting symmetrics
```bash
methpipe/methpipe-3.4.3/src/utils/symmetric-cpgs -v -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.symmetric_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth
```
Generating BigWig files
```bash
bedGraphToBigWig
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bedGraph mm10.chromeSizes
Epi1.bw
```

Getting bg
```bash
bedtools genomecov -ibam ICM_rep2_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -
bg | head
```
```bash
bedtools genomecov -ibam
../bedGraphs/Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -bg
```

Getting epicov.bg
```bash
bedtools genomecov -ibam
../Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -bg | cat > epicov.bg
```
Getting epi2cov.bw
```bash
bedGraphToBigWig epi2cov.bg mm10.chromeSizes epi2cov.bw
```
Getting methdiff
```bash
methpipe/methpipe-3.4.3/bin/methdiff -o Epiblast_Rep1_Rep2.methdiff
Epiblast_rep1_WGBS_R1_symmetric_CpGs.meth
Epiblast_rep2_WGBS_R1_symmetric_CpGs.meth
```
Generating hmr file
```bash
methpipe/methpipe-3.4.3/bin/hmr -o Epiblast_rep1.hmr
Epiblast_rep1_WGBS_R1_symmetric_CpGs.meth
```

```bash
Desktop/methpipe/methpipe-3.4.3/bin/dmr Epiblast_rep1_rep2.methdiff Epiblast_rep1.hmr
Epiblast_rep2.hmr \ DMR_rep1_lt_rep2 DMR_rep2_lt_rep1
```

### R Commands Used in generating histogram

```bash
hist(ICM_rep2_WGBS_R1_symmetric_CpGs.meth$V5, col="pink")
```

```bash
pdf(file="saving_ICM_rep2.pdf")
```

```bash
hist(ICM_rep2_WGBS_R1_symmetric_CpGs.meth$V5, col="pink")
dev.off()
```

### Links to Genome Browser Sessions

https://genome.ucsc.edu/cgi-bin/hgSession

https://genome.ucsc.edu/s/Josephluper/Epiblast_rep1_WGBS_1

https://genome.ucsc.edu/s/Josephluper/Epiblast_rep2_WGBS_1

https://genome.ucsc.edu/s/Josephluper/ICM_rep1_WGBS_1

https://genome.ucsc.edu/s/Josephluper/ICM_rep2_WGBS_1
