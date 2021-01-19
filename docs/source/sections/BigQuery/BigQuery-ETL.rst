How ISB-CGC BigQuery Tables are Created 
=======================================

The ISB-CGC team extracts, transforms, and loads data from cancer data repositories into Google BigQuery tables to make it easier to access for analysis.

Extract, Transform and Load (ETL)  process overview
---------------------------------------------------

The process differs slightly based on the source of the data (GDC, PDC, GENCODE, etc.) and the data type (RNA sequencing, Somatic Mutation, etc.) but generally, 
data are either gathered by using an Application Programming Interface (API) provided by the source for this purpose or by accessing files provided by the source.

Data for each program are consolidated by data type (ex. Clinical, DNA Methylation, RNAseq, Somatic Mutation, etc.) and transformed into ISB-CGC Google BigQuery tables. 
This novel approach allows our users to quickly analyze information from thousands of patients in our curated BigQuery tables.

ISB-CGC Workflow Components
+++++++++++++++++++++++++++

Each workflow is made up of the following files:

- YAML file (configuration file)
- Python files (extracts, transforms, and loads data)
- shell script file (runs the workflow)

GDC Workflows
-------------

.. list-table::
   :header-rows: 1 
   
   
   * - ISB-CGC Workflow
   * - GDC Case/File Metadata
   * - `GDC Clinical Data <ETL/ETL-GDC_Clinical.html>`_
   * - GDC RNA Seq
   * - GDC Open Somatic Mutation
   
   
.. toctree::
   :maxdepth: 1
   :hidden:
   
   ETL/ETL-GDC_Clinical

PDC Workflows
-------------

.. list-table::
   :header-rows: 1 
   
   
   * - ISB-CGC Workflow
   * - PDC Quant Data



Other Workflows
---------------

.. list-table::
   :header-rows: 1 
   
   
   * - ISB-CGC Workflow
   * - GENCODE
   
   
