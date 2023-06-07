## FASTQC  exercise

1. Go to the folder /home/intern/ocean
```r
cd /home/intern/ocean
```

2. List the folders present in this folder using ls. Count the number of samples (fastq files) using following cmd. Find out the number of samples with paired end data and the samples with single end data.
```r
ls PRJNA479567 | grep "SRR" | wc -l
```

3. Go inside the PRJNA* folders and perform fastqc. Use fastqc --help to understand the syntax. **Do not duplicate the analysis by performing same analyses from two logins inside same folder. cd to different PRJNA folders**.
```r
cd PRJNA479567
conda activate tutorial
fastqc *.fastq.gz -o /home/intern/ocean/fastqc
```

4. Downdoal the fastqc results (html files) and find out if they require trimming


