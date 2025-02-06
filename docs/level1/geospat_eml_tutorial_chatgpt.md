# Creating EML Metadata For Geospatial Data Using AI Chatbot Agents

## Background

The [Ecological Metadata Language (EML)](https://eml.ecoinformatics.org/) specification is widely used across domains in environmental research, conservation, and management. While there are tools for generating metadata for tabular and vector data using the EML specification, there exists a taller barrier of entry for geospatial data types (e.g., TIFF, GeoJSON, Shapefile, etc.). Here, we access the capacity for AI chatbot agents (e.g., ChatGPT, Claude, DeepSeek, CoPilot) to take geospatial data type inputs, extract metadata from the files, format the metadata according to the EML speficiation, and validate successfully on the ezEML web user interface (UI).

## What is ezEML?

[ezEML](https://ezeml.edirepository.org/eml/auth/login) is a web UI developed by the [Environmental Data Initiative (EDI)](https://edirepository.org/) designed to simplify the creation of metadata in the EML format. The ezEML UI guides users through the process of creating EML metadata, making it accessible even to those without extensive technical expertise. By streamlining the metadata creation and validation process, ezEML helps ensure that datasets are findable, accessible, interoperable, and reusable, facilitating data sharing and collaboration within the scientific community.

### How to: Upload XML To ezEML UI For Metadata Validation

1. **Access Web UI & Log In:** If you don't have an account, you may need to register or sign in using an institutional login if available.
2. **Navigate To Upload Section:** Look for an option or tab labeled "Upload" or "Import". This is typically found in the main navigation menu or dashboard.
3. **Upload XML File:** Click on the "Upload" or "Import" button to start the process. You will be prompted to select the XML file from your computer. Click on "Choose File" or "Browse" to locate your XML file. Select the XML file you wish to upload and click "Open".
4. **Validate XML File:** After uploading, ezEML will automatically begin the validation process. The tool will check the XML file against the EML schema to ensure it is correctly formatted and complete. 
5. **Review Results:** Once the validation is complete, ezEML will display the results. If there are any errors or warnings, they will be listed with details about what needs to be corrected. Review the feedback carefully. You may need to edit your XML file to address any issues.
6. **Edit & Re-upload (If Necessary):** If errors were found, use an XML editor to make the necessary corrections to your file. Save the changes and repeat the upload process to validate the corrected file.
7. **Finalize and Save:** Once your XML file passes validation without errors, you can proceed to save or publish your metadata within ezEML. Follow any additional prompts to complete the process, such as adding metadata details or linking to datasets.

## Experiments

For each experiment, the following variables are manipulated:

- Geospatial file type
- AI Chatbot Agent
- Prompt

The following method was followed for each experiment:

- Upload geospatial file to AI (if possible)
- Type prompt and execute
- Retrieve EML output either as downloadable XML file or text block that can be copied and saved as an XML File
- Visually inspect the outputs for general adherance to XML structure
- Upload XML, without modification to the ezEML web UI 

### Input Dataset Descriptions

#### LeafyLandscapesPlots

- This is a collection of observations of plant traits and biomass in a series of 211 one meter squared plots collected in 2024 by Ian Breckheimer at Rocky Mountain Biological Laboratory.. The dataset contains polygon geometries for each plot along with summarized field measurements for each plot.

<p align="center">
 <img width="450" alt="LeafyLandscapesPlots" src="https://github.com/user-attachments/assets/4eecd698-e1d8-4195-98a2-1de6db781a5b" />
</p>

#### IceTrafficDataFrame

This is a shapefile containing a polygon grid summarizing sea ice concentration data (CryoSat-2/SMOS Merged Product) and marine vessel counts (generated from Automatic Identification System vessel tracking data). Data are summarized on a monthly basis from January 2015 to December 2022 with one column per month. Data are projected in Alaska Albers (EPSG: There are >2,000 rows (one row per polygon) and >200 columns, making metadata generation a challenge.

<p align="center">
 <img width="450" alt="IceTrafficDataFrame" src="https://github.com/user-attachments/assets/10c09568-8488-4def-9a55-c3770fe21052" />
</p>

#### HLSL30.020_B01

This is a single-layer raster dataset representing one layer from a satellite image Band 2 (Blue) from the Harmonized Landsat - Sentinel 2 dataset. The image was collected in spring 2024 and shows a small mountainous area in Western Colorado. Although the primary data is public, this subset was extracted from the NASA APPEars web tool and has different properties from data already in the public domain.

<p align="center">
 <img width="450" alt="HLSL30 020 B01" src="https://github.com/user-attachments/assets/25e1e06b-3ed1-440d-ad0d-9bc4d9d35982" />
</p>

#### SeaIceVessel

These data represent a monthly time series of sea ice concentration data (CryoSat-2/SMOS Merged Product) and marine vessel counts (generated from Automatic Identification System vessel tracking data). Data are summarized on a monthly basis from January 2015 to December 2022 with one row per pixel per month. Vessel activity is measured as the total number of ships per pixel in a given month.

## Results

### Agent Compatibility By Geospatial File Type

|  | chatGPT-4o | Claude | DeepSeek | CoPilot |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Shapefile | Yes | No | No | No |
| GeoJSON | Yes | No (limited size) | Yes (limited size) | No |
| TIFF | Yes | No | Yes | No |
| CSV | Yes | Yes (limited size) | Yes | No |

### Results by Experiment

| File Type | Agent | Source Dataset | Prompt | Output | ezEML Validation | Notes |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| GeoJSON |	GPT4o |	LeafyLandscapesPlots |	Please generate metadata in the EML version 2.2 format for the LeafyLandscapesPlots geoJSON file. |	XML embedded text | Partial | Lacking bounding box coordinates | 	
| Shapefile | GPT4o | IceTrafficDataFrame | Please generate metadata in the EML version 2.2 format for the IceTrafficDataFrame shapefile. | XML Download | Partial | Bounding box in incorrect project, lacking creator and contributor |
| TIFF | Deepseekv-3 | HLSL30.020_B01 | Please generate metadata in the EML version 2.2 format for the attached data | XML embedded text | Minimal | Support tiff format and successful EML metadata but not well-populated |
| TIFF | GPT4o | HLSL30.020_B01 | Please generate metadata in the EML version 2.2 format for the HLSL30.020_B01.tif TIFF file. | XML embedded text | Minimal | Only image size information extracted. Hallucinated image date |
| CSV | GPT4o | SeaIceVessel | Please generate metadata in the EML version 2.2 format for the SeaIceVessel csv | XML embedded text | Partial | Missed some column names |
| CSV | DeepSeek | SeaIceVessel | Please generate metadata in the EML version 2.2 format for the SeaIceVessel csv | XML embedded text | Partial | Complete columns, but put "dimensionless" ratio for numeric data |

### Screenshots

#### Experiment: GeoJSON uploaded to GPT4o

**Prompt:**
<p align="center">
 <img width="500" alt="LeafyLandscapesPlots-GPT4o-GeoJSON" src="https://github.com/user-attachments/assets/82b1dbdc-1e69-45c4-85e6-17a8eee83833" />
</p>

**ezEML UI:**
<p align="center">
 <img width="500" alt="LeafyLandscapesPlots-GPT4o-GeoJSON_ezEML_validation" src="https://github.com/user-attachments/assets/afd0b4de-37b4-4a7c-996b-dd840a7f083e" />
</p>

#### Experiment: Shapefile uploaded to GPT4o

**Prompt:**
<p align="center">
 <img width="500" alt="IceTrafficDataFrame-GPT4o-shp-GPToutput" src="https://github.com/user-attachments/assets/341818e3-ef66-44ec-b7d9-a4f3f7d01f4d" />
</p>

**ezEML UI:**
<p align="center">
 <img width="500" alt="IceTrafficDataFrame-GPT4o-shp-ezEML" src="https://github.com/user-attachments/assets/2869034b-117d-4d30-ae9f-1ca1309a9339" />
</p>

## Discussion

## Conclusion

## Authors & Awknowledgements

This tutorial was generated by a group of collaborators participating in the 2025 Environmental Data Science Summit hosted by the National Center for Environmental Analysis and Synthesis in Santa Barbara, California.

**Contributors**

- Ian Breckheimer, Rocky Mountain Biological Station, 
- Kelly Kapsar, Michigan State University, 
- Unis, 
- Zachary Nickerson, National Ecological Observatory Network, nickerson@battelleecology.org 
