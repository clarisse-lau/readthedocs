GDC Clinical Data Workflow
==========================

The data in the clinical_gdc_XX tables (example: isb-cgc-bq:BEATAML1_0.clinical_gdc_current) is pulled from the GDC API.

Overview of the ISB-CGC ETL steps:

- For every case available from the cases endpoint, the following field groups are requested and added to a master BigQuery table: 

  * demographic
  * diagnoses, diagnoses.treatments, diagnoses.annotations
  * exposures
  * family_histories
  * follow_ups, follow_ups.molecular_tests
  * project
  
- Field descriptions are retrieved from the cases mapping endpoint, for inclusion in the final table schemas. (Some fields have null descriptions or require more detail. In this case, the column descriptions are modified after BQ table generation using a JSON definition file.)

- The data contained in each field is evaluated to determine its schema type definition. (Example: not every sequence of numeric digits should be considered an INTEGER type--if the sequence contains a leading zero, as is sometimes the case for id fields, INTEGER typing would result in data loss.)

- Each case is mapped to its corresponding program using the GDC case metadata table. The following steps occur on a per-program basis.

- Lauren’s note to self: to be continued -- flattening/deriving tables
