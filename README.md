# DNA Methylation Analysis (Transcriptomics and Epigenetics Project)

### By Joseph Luper Tsenum

Email: tsenumjosephluper@phystech.edu

Phystech School of Biological and Medical Physics (FBMF)
Moscow Institute of Physics and Technology (National Research University)

Russian Federation


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

```methpipe/methpipe-3.4.3/bin/analysis/methcounts -cpg-only -c mouse_chr/chr19.fa -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated```

```methpipe/methpipe-3.4.3/src/analysis/methcounts -cpg-only -c mouse_chr/chr19.fa -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.mr```

```methpipe/methpipe-3.4.3/src/utils/symmetric-cpgs -v -o
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.symmetric_CpGs.meth
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.all_CpGs.meth```

```bedGraphToBigWig
Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bedGraph mm10.chromeSizes
Epi1.bw```

```bedtools genomecov -ibam ICM_rep2_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -
bg | head```

```bedtools genomecov -ibam
../bedGraphs/Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -bg```

```bedtools genomecov -ibam
../Epiblast_rep1_trimmed_WGBS_R1_bismark_bt2_pe.deduplicated.bam -bg | cat > epicov.bg```

```bedGraphToBigWig epi2cov.bg mm10.chromeSizes epi2cov.bW```

```methpipe/methpipe-3.4.3/bin/methdiff -o Epiblast_Rep1_Rep2.methdiff
Epiblast_rep1_WGBS_R1_symmetric_CpGs.meth
Epiblast_rep2_WGBS_R1_symmetric_CpGs.meth```

```methpipe/methpipe-3.4.3/bin/hmr -o Epiblast_rep1.hmr
Epiblast_rep1_WGBS_R1_symmetric_CpGs.meth```

```Desktop/methpipe/methpipe-3.4.3/bin/dmr Epiblast_rep1_rep2.methdiff Epiblast_rep1.hmr
Epiblast_rep2.hmr \ DMR_rep1_lt_rep2 DMR_rep2_lt_rep1```

R Commands Used in generating histogram

```hist(ICM_rep2_WGBS_R1_symmetric_CpGs.meth$V5, col="pink")```

```pdf(file="saving_ICM_rep2.pdf")```

```hist(ICM_rep2_WGBS_R1_symmetric_CpGs.meth$V5, col="pink")
dev.off()```

Links to Genome Browser Sessions

https://genome.ucsc.edu/cgi-bin/hgSession

https://genome.ucsc.edu/s/Josephluper/Epiblast_rep1_WGBS_1

https://genome.ucsc.edu/s/Josephluper/Epiblast_rep2_WGBS_1

https://genome.ucsc.edu/s/Josephluper/ICM_rep1_WGBS_1

https://genome.ucsc.edu/s/Josephluper/ICM_rep2_WGBS_1
