# 🧮 Step 08: Generate Gene Counts Using FeatureCounts

## 🎯 Why Do We Do It?
After alignment and BAM processing, the next step is to **quantify gene expression** by counting the number of reads mapping to genes or exons. `featureCounts` is a fast and accurate tool from the Subread package designed specifically for this task.

---


## 🔧 Tool: `featureCounts` (from Subread)

- For **gene/exon count matrix**, download reference annotation (e.g., from GENCODE) matching your genome build.
- Use `featureCounts` with sorted BAM and annotation files.


---


## 🛠️ Command

```
featureCounts -T 4 -p -t exon -g gene_id -a /home/vzscyborg/ngs/mouse/gencode.vM37.primary_assembly.basic.annotation.gff3 -o /home/vzscyborg/ngs/mouse/fc/counts.txt /home/vzscyborg/ngs/mouse/smtl/30sorted.bam /home/vzscyborg/ngs/mouse/smtl/31sorted.bam /home/vzscyborg/ngs/mouse/smtl/34sorted.bam /home/vzscyborg/ngs/mouse/smtl/35sorted.bam
```
### 🧾 Parameters

- featureCounts: program from the Subread package used to count reads mapped to genomic features (like genes or exons). 
- -T 4: 	Use 4 CPU threads for faster performance.  
- -t exon: 	Count exons as the feature type. Only lines with feature type == exon in the GTF file will be used. 
- -g gene_id: 	Group exons by the gene_id attribute from the GTF file to produce gene-level counts. 
- -a:  Path to the GTF annotation file, used to define the gene and exon features. 
- -o: 	Output file name where the read counts per gene will be saved.
- 	Input sorted BAM files (your aligned reads) that will be counted.

---
## ✅ Output
A count matrix in tab-delimited format:
/home/vzscyborg/ngs/mouse/fc/counts.txt

This matrix will serve as the input for downstream differential expression or transcriptomic analyses.
