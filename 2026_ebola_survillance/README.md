# Ebolya Mayinga Survaillance

## Projekt ID's
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

Creating the fastq,bam and vcf files [SRR=SRR1553425]
```
# Step 2: For downloading the reads from SRA, limit to limit

make fastq


# Step 3: Align your fastq files into a bam file

make align


# Step 4: Create vcf files

make vcf
```

## If you want to use other SRR file or limits:
```
#Cleaning the old files
make clean

# I recomend these good quality samples: SRR1972976 | SRR1553426
# Using other SRR number
make fastq align vcf SRR = 

# Using other limit
make fastq align vcf LIMIT=

# You can combine it if needed
make fastq align vcf LIMIT=  SRR=
```


