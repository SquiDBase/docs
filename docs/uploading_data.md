# Uploading Data to SquiDBase

Before uploading data to SquiDBase, you need to create an account. This ensures that each dataset is linked to a submitter and a principal investigator (PI) or responsible person.  

You can sign up directly [here](https://squidbase.org/account/register) or visit the SquiDBase website, click **"Sign in"** in the top-right corner, and select **"Sign up here"**.

---

## Checklist before upload

Before proceeding with your upload, please ensure that your data meets the following requirements:

- The data must be of **microbial or viral origin** and **must not contain human data** to comply with privacy regulations. Metadata must also be free of patient-identifiable information.  
- Each upload should originate from **a single Nanopore sequencing chemistry**. This information is automatically extracted from your **POD5** files during upload.  
- Metadata should be as complete as possible. **Once uploaded, metadata cannot be modified**, except for the **info field**, which remains editable.  

Once your data meets these criteria, you have two options:
1. If each POD5 file contains only one biological species, you can proceed with the [upload process filtered data](#upload-when-data-is-already-filtered).  
2. Alternatively, if your dataset contains a mix of viral or microbial species, you can **filter out POD5 reads per species** using **SquiDPipe**, a dedicated pipeline designed for this purpose. These steps are explained under [upload process mixed data](#upload-of-mixed-datasets-–-running-squidpipe)

---

## Upload when data is already filtered

If your data has already been filtered (i.e., **each POD5 file contains reads from only one microbial or viral species**), you only need to upload:  

1. The **POD5 files**  
2. A **CSV file with the corresponding metadata**  

### Metadata CSV File Format

Your metadata CSV file should follow the format below. If any metadata is missing, enter **"NA"** in the respective field.  

**Accepted delimiters:** `,` and `;`  

A **template CSV file** is available for download: [Download Template](assets/full.csv).  

#### Example Metadata Format  

| filename   | species_name    | species_taxid | year_of_isolation | country_of_isolation | geographic_origin | strain_lineage | source_id | host_taxid | internal_lab_id | diagnostic_method_id | remarks         |
|------------|---------------|--------------|-------------------|--------------------|----------------|--------------|----------|-----------|----------------|-------------------|----------------|
| file1.pod5  | DENV          | 11053        | 2014              | NA                 | NA             | ECSA         | NA       | NA        | NA             | NA                | ITM collection |
| file2.pod5  | HIV           | 11676        | 2015              | BE                 | NI             | ECSA         | NA       | NA        | NA             | NA                | ITM collection |
| file3.pod5  | ZIKV          | 64320        | 11053             | 2015               | BE             | ID           | NA       | NA        | NA             | NA                | NA             |
| file4.pod5  | SARS-CoV-2_A  | 2697049      | 11060             | 2018               | BE             | PE           | NA       | NA        | NA             | NA                | NA             |
| file5.pod5  | SARS-CoV-2_B  | 2697049      | 11060             | 2018               | BE             | PE           | NA       | NA        | NA             | NA                | NA             |

---

## Upload of mixed datasets – running SquiDPipe 

Many **Nanopore sequencing runs**, particularly those involving barcoded samples with multiple microbial or viral species, **contain mixed species per POD5 file**.  

To handle this, use **SquiDPipe**, an **extflow pipeline** designed to process barcoded runs, including **FASTQ files**. It will:  

- Classify reads based on the **basecalled sequences**  
- Automatically **separate POD5 files** by species  

For instructions on running **SquiDPipe**, visit:  
[**SquiDPipe GitHub Repository**](https://github.com/Cuypers-Wim/squidpipe)
