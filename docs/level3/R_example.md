# Using LLMs in R Code

## Use Case

Here, we will use an example of structured data extraction to illustrate integrating LLMs into a custom end-to-end pipeline. In ecological research, extracting specific data from scientific papers can be time-consuming. Leveraging Large Language Models (LLMs) can streamline this process. We'll use the [ellmer package](https://ellmer.tidyverse.org/) to extract information from PDFs and generate a table. The table will summarize population trends of species based on the literature. This example uses the LLM feature of [structured data](https://ellmer.tidyverse.org/articles/structured-data.html). While it is possible to complete this task using a browser-based chatbot, including the LLM in your code with your prompt makes your work more reproducible.

## Prerequisites

Ensure you have the following R packages installed:

- `ellmer`: Facilitates interaction with LLMs.
- `pdftools`: Enables text extraction from PDFs.

Install them using:

```r
install.packages("ellmer")
install.packages("pdftools")
```

## Setting Up the Environment

Begin by loading the necessary libraries and setting your OpenAI API key:

```r
library(ellmer)
library(pdftools)

# Set your OpenAI API key
Sys.setenv(OPENAI_API_KEY = "your-secret-key")
```

Replace `"your-secret-key"` with your actual OpenAI API key.

## Extracting Text from the PDF

Define the path to your PDF file and extract its text content:

```r
# Specify the path to your PDF file
pdf_file <- "path/to/your/cn2.pdf"

# Extract text from the PDF
pdf_text <- pdf_text(pdf_file)

# Display the extracted text
print(pdf_text)
```

Ensure that the `pdf_file` variable points to the correct location of your PDF document.

## Defining the Data Structure

Outline the structure of the data you aim to extract. In this case, we're interested in species population trends:

```r
# Define the expected data structure
type_summary <- type_array(
  "An array containing a row for every species for which a trend in population through time is mentioned",
  items = type_object(
    "Data on trends through time for a single species",
    title = type_string("Title of the paper"),
    species = type_string("Name of the species"),
    trend = type_string("Population trend through time. Must be either 'increasing', 'decreasing', or 'no trend'. No other options are permitted")
  )
)
```

This structure specifies that for each species mentioned in the paper, we want to extract the title, species name, and population trend.

## Extracting Data Using the LLM

Utilize the `ellmer` package to extract the structured data from the PDF text:

```r
# Initialize the chat interface with the specified model
chat <- chat_openai(model = 'gpt-4o-mini')

# Extract data based on the defined structure
data <- chat$extract_data(pdf_text, type = type_summary)

# Display the extracted data
print(data)
```

The `chat$extract_data` function processes the extracted PDF text and retrieves data matching the defined structure.

## Conclusion

By following this approach, you can efficiently extract structured ecological data from scientific PDFs using LLMs, thereby enhancing your research workflow.

**Note:** Ensure that your PDF file is accessible and that your OpenAI API key is valid. This method leverages the capabilities of LLMs to automate data extraction, making the research process more efficient. 
