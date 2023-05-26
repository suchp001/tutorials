# Working with Qiime2 output

## Exercises
1. Load the necessary packages in R, including the `tidyverse` package.
2. Read the QIIME taxa table file, named "taxa_table.txt", into a tibble.
3. Display the first 5 rows of the taxa table.
4. Filter the taxa table to include only the rows where the "Kingdom" column is "Bacteria".
5. Remove the "Confidence" column from the taxa table.
6. Group the taxa table by the "Phylum" column and calculate the mean abundance for each phylum.
7. Sort the taxa table by the mean abundance in descending order.
8. Create a new column in the taxa table called "Proportion" that represents the proportion of each taxon's abundance relative to the total abundance.
9. Create a new column in the taxa table called "Rank" that indicates the taxonomic rank of each taxon based on the number of columns present.
10. Write the transformed taxa table to a new file named "transformed_taxa_table.txt" in the QIIME-compatible format.


## Solutions
1. Load the necessary packages in R, including the `tidyverse` package.
```R
library(tidyverse)
```

2. Read the QIIME taxa table file, named "taxa_table.txt", into a tibble.
```R
taxa_table <- read_qza("taxa_table.txt")$data %>%
  as_tibble()
```

3. Display the first 5 rows of the taxa table.
```R
head(taxa_table)
```

4. Filter the taxa table to include only the rows where the "Kingdom" column is "Bacteria".
```R
filtered_taxa_table <- taxa_table %>%
  filter(Kingdom == "Bacteria")
```

5. Remove the "Confidence" column from the taxa table.
```R
taxa_table <- taxa_table %>%
  select(-Confidence)
```

6. Group the taxa table by the "Phylum" column and calculate the mean abundance for each phylum.
```R
mean_abundance <- taxa_table %>%
  group_by(Phylum) %>%
  summarize(mean_abundance = mean(Abundance))
```

7. Sort the taxa table by the mean abundance in descending order.
```R
sorted_taxa_table <- taxa_table %>%
  arrange(desc(Abundance))
```

8. Create a new column in the taxa table called "Proportion" that represents the proportion of each taxon's abundance relative to the total abundance.
```R
taxa_table <- taxa_table %>%
  mutate(Proportion = Abundance / sum(Abundance))
```

9. Create a new column in the taxa table called "Rank" that indicates the taxonomic rank of each taxon based on the number of columns present.
```R
taxa_table <- taxa_table %>%
  mutate(Rank = rowSums(!is.na(.)) - 1)
```

10. Write the transformed taxa table to a new file named "transformed_taxa_table.txt" in the QIIME-compatible format.
```R
write_qza(taxa_table, "transformed_taxa_table.qza")
```
