# RNA-Seq Analysis with the HiSat2 aligner
In this folder you can download the Universal Human Reference (UHR) genom and the Human Brain Reference (HBR). Makefile will help to create the files needed to visualize the alignments and visualize the coverages. Also with this makefile you will be able to do some basic statistic and export it to a csv file format. 

## Project ID's
Article URL = https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1004393 \
For important variables
```
make help
```

## Projekt steps
Add the tools if you dont already have it
```
pixie add bwa samtools src sra-tools hisat2 subread curl 
```

Downloading the data -> indexing it -> align it
```
# Step 1: Download
make download 

# Step 2 : Index
make index

# Step 3: Align
make align
```

Count the alignments over the features -> into CSV -> edgeR analysis
```
# Step 4: Counting
make count

# Step 5: Reformat counting into CSV
make to_csv

# Step 6: Add gene names to counts file
make add_names

# Step 7:
make edger
```

Generating PCA plot, heatmap and deign file
```
# Step 8: generate PCA plot
make pca

# Step 9: generate heatmap
make heatmap

# Step 10: Show design file
make design
```

## If you want to use other SRR file & extra
For using...