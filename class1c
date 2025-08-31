#assignment 2 
getwd()
setwd("path to your folder)
read.csv(file.choose())
# 1. Function to classify genes
classify_gene <- function(logFC, padj) {
  if (is.na(padj)) padj <- 1      # Replace NA padj with 1
if (logFC > 1 & padj < 0.05) {
     return("Upregulated")
} else if (logFC < -1 & padj < 0.05) {
    return("Downregulated")
} else {
    return("Not_Significant")
}
}
# 2. Prepare file names
input_files <- c("DEGs_Data_1.csv", "DEGs_Data_2.csv")
output_folder <- "Results"
dir.create(output_folder, showWarnings = FALSE)
# 3. For-loop over both datasets
for (file in input_files) {
# Load data
df <- read.csv(file.choose())
# Replace missing padj values with 1
df$padj[is.na(df$padj)] <- 1 
print(head())
# Add 'status' column using the classify_gene function
df$status <- mapply(classify_gene, df$logFC, df$padj)
# Save processed file
output_file <- file.path(output_folder, paste0("Processed_", file))
write.csv(df, output_file, row.names = FALSE)
cat("Summary for", file, "\n")
print(table(df$status)) # Counts of each status
cat("\n") 
save.image(file = "IQRAREHMAN_class_2_assignment.RData") 

