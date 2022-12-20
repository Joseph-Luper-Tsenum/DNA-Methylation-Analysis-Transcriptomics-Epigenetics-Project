# CpG Methylation in Early Mouse Embryonic Development WGBS Samples - (Sequencing of the Whole Bisulfite Genome)

### By Joseph Luper Tsenum

Email: tsenumjosephluper@phystech.edu

Phystech School of Biological and Medical Physics (FBMF)

Moscow Institute of Physics and Technology (National Research University)

Russian Federation

### Introduction

Whole genome bisulfite sequencing (WGBS) experiments carried out on mouse embryogenic cells by Smith et al. 2017 were analyzed. inner cell mass (ICM) and epiblast were selected for analysis.

From the analysis conducted on ICM and Epiblast, while ICM cells were hypomethylated more, epiblast were hypermethylated more. From my bismark extraction result, it can be seen that the percentage of methylation CpGs in epiblast far exceeds that of ICM in both replicates. This means that epiblast has been methylated more than ICM. On the otherhand, the number of unmethylated C's in CpG context of ICM is in abundance compared to epiblast unmethylated C's in CpG context. This means that ICM is hypomethylated while epiblast is hypermethylated. This confirms the believe that during the development of the embryo, CpG methylation decreases (about 25%) in the early stages as can be seen here in the case of ICM while during tissue differentiation, the CpG content increases significantly (about 90%) and remains throughout the life of the body as we can see here in the case of epiblast. This means that CpG methylation plays a crucial role in ICM cells pluripotency and cell differentiation. This therefore accounts for the global reduction levels of CpGs in the inner cell mass (ICM) which is accompanied by undetectable levels of DNA methyltransferase of each class in the nuclei of ICM while the levels of CpGs in epiblast increases as cell differentiation occurs.

Chromosome Used: Chromosome 19 of Genome mm10 was used for alignment. 

FastQC Reports for the three samples

![now3](https://user-images.githubusercontent.com/58364462/208570425-f20bb816-8e73-4e6c-90ed-caaddde1ed94.png)


### Bismark Report

Bismark statistics

![now4](https://user-images.githubusercontent.com/58364462/208570667-c76bd918-6545-422d-9ab0-04be72ae27c0.png)


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

### UCSC Genome Browser, cytosine Methylation and coverage overview at position chromosome 19 as shown below:

![image](https://user-images.githubusercontent.com/58364462/208539403-92a3a3bc-d16d-471f-887a-9f8c68ba3ab8.png)

![image](https://user-images.githubusercontent.com/58364462/208539478-494079fe-21ca-430c-bfd5-f5ee3eb6d0ca.png)

![image](https://user-images.githubusercontent.com/58364462/208539514-8a9249f5-b42a-455d-b920-074eb502dce1.png)

![image](https://user-images.githubusercontent.com/58364462/208539551-92b215bc-bb9a-4762-a8cf-fb97f72c3935.png)


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
Each step above was carried out on all the four samples

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


### References

1. Smith ZD, Shi J, Gu H, Donaghey J, Clement K, Cacchiarelli D, Gnirke A, Michor F, Meissner A. Epigenetic restriction of extraembryonic lineages mirrors the somatic transition to cancer. Nature. 2017 Sep 28;549(7673):543-547. doi: 10.1038/nature23891. Epub 2017 Sep 20. PMID: 28959968; PMCID: PMC5789792.

2. Krueger F, Andrews SR. Bismark: a flexible aligner and methylation caller for Bisulfite-Seq applications. Bioinformatics. 2011 Jun 1;27(11):1571-2. doi: 10.1093/bioinformatics/btr167. Epub 2011 Apr 14. PMID: 21493656; PMCID: PMC3102221.

3. Kent WJ, Zweig AS, Barber G, Hinrichs AS, Karolchik D. BigWig and BigBed: enabling browsing of large distributed data sets. Bioinformatics. 2010 Sep 1;26(17):2204-7.

4. Kent WJ, Sugnet CW, Furey TS, Roskin KM, Pringle TH, Zahler AM, Haussler D. The human genome browser at UCSC. Genome Res. 2002 Jun;12(6):996-1006.

5. Song Q, Decato B, Hong E, Zhou M, Fang F, Qu J, Garvin T, Kessler M, Zhou J, Smith AD (2013) A reference methylome database and analysis pipeline to facilitate integrative and comparative epigenomics. PLOS ONE 8(12): e81148 [PDF] [Publisher Site]

6.   R Core Team (2018). R: A language and environment for statistical computing. R Foundation for Statistical Computing, Vienna, Austria. URL https://www.R-project.org/.


