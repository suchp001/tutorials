## phyloseq tutorial

Exercise: Exploring Microbial Diversity with Phyloseq

1.  Install the `phyloseq` package

2.  Load the `phyloseq` library:
```r
library(phyloseq)
```

3.  Download the example dataset provided by `phyloseq` called "GlobalPatterns":
```r
data(GlobalPatterns)
```

4.  Explore the dataset by examining its components:
```r  
# View the OTU table
otu_table(GlobalPatterns)

# View the sample data
sample_data(GlobalPatterns)

# View the taxonomic data
tax_table(GlobalPatterns)
```

5.  Calculate alpha diversity measures:
```r  
# Calculate observed OTUs
observed <- estimate_richness(GlobalPatterns)

# Calculate Shannon diversity
shannon <- estimate_richness(GlobalPatterns, measures = "Shannon")

# View the results
observed
shannon
```

6. Plot observed richness:
```r  
# Bar plot of observed richness
barplot(observed$Observed, axisnames = T, main = "observed", xlab = "Samples", ylab = "Richness")

# Shannon diversty
samples <- rownames(shannon)
barplot(shannon$Shannon, main = "Shannon Diversity", names.arg = samples, xlab = "Samples", ylab = "Diversity")
```

7.  Plot alpha diversities by sample-type
```r
# Calculate alpha diversity measures for each sample:
alpha_diversity <- estimate_richness(GlobalPatterns)

# Extract the alpha diversity values and corresponding sample metadata:
diversity_values <- alpha_diversity[, "Shannon"]
sample_metadata <- sample_data(GlobalPatterns)

# Merge the alpha diversity values with the sample metadata:
alpha_df <- data.frame(Sample = rownames(sample_metadata), AlphaDiversity = diversity_values)
colnames(alpha_df) <-  c("X.SampleID", "AlphaDiversity")
sample_data <- data.frame(sample_metadata)
merged_data <- merge(sample_data, alpha_df, by = "X.SampleID")

# Create a box plot of sample-specific alpha diversity based on the "SampleType" metadata:
boxplot(AlphaDiversity ~ SampleType, data = merged_data, 
        main = "Sample-Specific Alpha Diversity", xlab = "Sample Type", ylab = "Alpha Diversity")
```

8.  Visualise the data using PCoA analysis:
```r
# Calculate Bray-Curtis dissimilarity
bray_curtis <- distance(GlobalPatterns, method = "bray")

# Perform Principal Coordinate Analysis (PCoA)
pcoa <- ordinate(GlobalPatterns, method = "PCoA", distance = bray_curtis)

# Visualize the PCoA
plot_ordination(GlobalPatterns, pcoa, color = "SampleType")
```

