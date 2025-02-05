# Creating EML Metadata for Geospatial Data using ChatGPT

## Background

The Ecological Metadata Language (EML) specification is widely used across domains in environmental research, conservation, and management. While there are tools for generating metadata for tabular and vector data using the EML specification, there exists a taller barrier of entry for geospatial data types (e.g., TIFF, GeoJSON, Shapefile, etc.). Here, we access the capacity for AI chatbot tools (e.g., ChatGPT, Claude, DeepSeek, CoPilot) to take geospatial data type inputs, extract metadata from the files, format the metadata according to the EML speficiation, and validate successfully on the ezEML web user interface (UI).

## What is ezEML?

ezEML is a web UI designed to simplify the creation of metadata in the EML format. The ezEML UI guides users through the process of creating EML metadata, making it accessible even to those without extensive technical expertise. By streamlining the metadata creation and validation process, ezEML helps ensure that datasets are findable, accessible, interoperable, and reusable, facilitating data sharing and collaboration within the scientific community.

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

**LeafyLandscapesPlots**

- *description*

**IceTrafficDataFrame**

- *description*

**HLSL30.020_B01**

- *description*

### Overall Results

**Table 1:** Geospatial file types accepted by AI Chatbot Agent
 
| File Type | **chatGPT-4o** | **Claude** | **DeepSeek** | **CoPilot** |
|  | ----------- | ----------- | ----------- | ----------- |
| *Shapefile* | Yes | No | No | No |
| *GeoJSON* | Yes |  |  |  |			
| *TIFF* |  |  |  |  |				
| *CSV* |  |  |  |  |

### 