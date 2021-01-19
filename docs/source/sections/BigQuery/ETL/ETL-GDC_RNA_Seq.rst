GDC RNA Seq Workflow
==========================

The data in the RNAseq_hgXX_gdc_XX tables (example: isb-cgc-bq.BEATAML1_0.RNAseq_hg38_gdc_current) is from the Genomic Data Commons. 
Please visit the GDC documentation for more information on the GDC mRNA Sequencing Pipeline.

Overview of the ISB-CGC ETL steps:

- A list of RNA seq files is created for the RNAseq tables from a table in the  GDC_case_file_metadata_versioned data set

  * more information on metadata workflow here
  * The version of GDC metadata used is typically the same as the GDC data release the data was released in, if another metadata table was used, it is noted in the table description

- The files are downloaded from the GDC Google Cloud Buckets using their Google Storage (GS) URL which is gathered from the GDC metadata BigQuery Tables
- Individual files are joined into one file for each gene expression count type
- The expression count data is transferred to BigQuery tables
- Extra data from GENCODE v22 and the GDC metadata tables are added to each expression count table.

  * Added columns are: project, case barcode and id, sample barcode and id, aliquot barcode and id, primary site, gene name, gene type, and platform
  
- The expression count tables are merged into one table with each sequencing count type in its own column along with the added extra data
- The table schema is updated
- The table is then reviewed and published to the isb-cgc-bq project
