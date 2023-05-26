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


