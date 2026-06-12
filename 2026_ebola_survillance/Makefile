# Változók
# The URL to the genome.
FASTA_URL=https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/848/505/GCF_000848505.1_ViralProj14703/GCF_000848505.1_ViralProj14703_genomic.fna.gz

# The URL to the annotation.
GFF_URL=https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/848/505/GCF_000848505.1_ViralProj14703/GCF_000848505.1_ViralProj14703_genomic.gff.gz

# Name of he genome
GENOME_NAME = ebola

# Path of the genome fasta & gff files
GENOME_FASTA = data/${GENOME_NAME}.genom.fna
GENOME_GFF = data/${GENOME_NAME}.annotation.gff


# The SRR ID of the sample 
SRR = SRR1553425

# The name of the alignment file
BAM = bam/${SRR}-${GENOME_NAME}.bam

# The number of reads
LIMIT=10000

# the path of the reads file
R1 = reads/${SRR}_1.fastq
R2 = reads/${SRR}_2.fastq



#---------------------NO CHANGES BELOW THIS LINE---------------------
help:
	@echo "Olvasd el a Makefile-t"

#Run download than fastq than align
start: download fastq align vcf

#IF I want a new SRR numbered run
new_srr: fastq align vcf

#make the directories that are needed then download and unzip the fasta and gff files
download: ${GENOME_FASTA} ${GENOME_GFF}

${GENOME_FASTA}:
	mkdir -p data
	wget -O $@.gz ${FASTA_URL}
	gunzip -f $@.gz
	bwa index ${GENOME_FASTA}

${GENOME_GFF}:
	mkdir -p data
	wget -O $@.gz ${GFF_URL}
	gunzip -f $@.gz

# Use fastq-dump to download the reads from SRA, limit to limit
fastq:
	mkdir -p reads
	fastq-dump --split-files --outdir reads --maxSpotId ${LIMIT} ${SRR}

# Align the reads to the genome anf sort the bam file
align:
	mkdir -p bam
	bwa mem -t 4 ${GENOME_FASTA} ${R1} ${R2} | \
		samtools sort --write-index -o ${BAM}
	samtools flagstat ${BAM}

#vcf
vcf:
	make -f src/run/bcftools.mk REF=${GENOME_FASTA} BAM=${BAM} run

#clean
clean:
	rm -rf bam reads vcf data


.PHONY: download fastq	vcf




