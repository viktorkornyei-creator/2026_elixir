# Ebolya Mayinga Survaillance
With this makefile you can download the reference genom of Ebola mayinga virus and create the files needed to compare it with other Ebola mayinga sequences visually

## Project ID's
URL = https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000848505.1/ \
SRA Bio Project ID: PRJNA257197 \
NCBI ebola ID: GCF_000848505.1 \
metadata ID: SRR1553425

## Projekt steps
Add the tools if you dont already have it
```
pixie add bwa samtools src sra-tools
```

Download (and index) the data
```
# Step 1: Download the data
make download
```

Creating the fastq, bam and vcf files [SRR=SRR1553425; LIMIT=10000]
```
# Step 2: For downloading the reads from SRA, limit to limit

make fastq


# Step 3: Align your fastq files into a bam file

make align


# Step 4: Create vcf files

make vcf
```
### Cleaning and quick starting projekt
For **cleaning all of your downloaded data** and SRR related files in this projekt
```
make clean all
```

Quick starting the projekt and running all of the steps
```
# It is recommended that you have already run the project at least once (this will include steps 1-4)
make start
```

## If you want to use other SRR file or limits:
For other SRR file:
```
# Cleaning the old files
make clean-SRR

# I recomend these good quality samples: SRR1972976 | SRR1553426
# Using other SRR number ~ variable: {SRR} =
make fastq align vcf SRR=
```
For other limit:
```
# Cleaning the old files
make clean-SRR

# Using other limit ~ variable: {LIMIT} =
make fastq align vcf LIMIT=
```
For other SRR file and limit:
```
# Cleaning the old files
make clean-SRR

# You can combine it if needed ~ variable {LIMIT} and {SRR}
make fastq align vcf LIMIT=  SRR=
```



