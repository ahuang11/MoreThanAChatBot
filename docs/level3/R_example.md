# Using LLMs in R Code

## Use Case
Here, we will use an example of [structured data](https://ellmer.tidyverse.org/articles/structured-data.html) extraction to illustrate integrating LLMs into a custom end-to-end pipeline. In ecological research, extracting specific data from scientific papers can be time-consuming. Leveraging Large Language Models (LLMs) can streamline this process. This guide demonstrates how to use the [ellmer package](https://ellmer.tidyverse.org/) in R to extract species population trends from a PDF document. While it is possible to complete this task using a browser-based chatbot, including the LLM in your code with your prompt makes your work more reproducible.

## Prerequisites

Ensure you have the following R packages installed:

- `ellmer`: Facilitates interaction with LLMs.
- `pdftools`: Enables text extraction from PDFs.
- `purrr`: Iterate extraction over multiple PDFs.

Install them using:

```r
# Install packages
install.packages("ellmer")
install.packages("pdftools")
install.packages("purrr")
```

## Setting Up the Environment

Begin by loading the necessary libraries and setting your OpenAI API key:

```r
# Load packages
library(ellmer)
library(pdftools)
library(purrr)

# Set your OpenAI API key
Sys.setenv(OPENAI_API_KEY = "your-secret-key")
```

Replace `"your-secret-key"` with your actual OpenAI API key.

## Downloading the PDFs

We've assembled freely-available PDFs for this example [here](https://github.com/ahuang11/MoreThanAChatBot/tree/main/docs/level3/pdf). Download them and save them to a folder called "pdf".
```r
# Download PDFs
download.file("https://github.com/ahuang11/MoreThanAChatBot/blob/main/docs/level3/pdf/paper1.pdf",
  "pdf/paper1", mode = "wb")
download.file("https://github.com/ahuang11/MoreThanAChatBot/blob/main/docs/level3/pdf/paper2.pdf",
  "pdf/paper2", mode = "wb")
download.file("https://github.com/ahuang11/MoreThanAChatBot/blob/main/docs/level3/pdf/paper3.pdf",
  "pdf/paper3", mode = "wb")
download.file("https://github.com/ahuang11/MoreThanAChatBot/blob/main/docs/level3/pdf/paper4.pdf",
  "pdf/paper4", mode = "wb")

```

## Extracting Text from the First PDF

Paper 1 describes trends for multiple species. Ensure that the path to the PDF is correct and extract its text content:

```r
# Specify the path to your PDF file
pdf1 <- "pdf/paper1.pdf"

# Extract text from the PDF
pdf_text1 <- pdf_text(pdf1)

# Display the extracted text
print(pdf_text1)
```

## Defining the Data Structure for Trends

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

## Extracting Trends Using the LLM

Utilize the `ellmer` package to extract the structured data from the PDF text. We use the OpenAI gpt-4o-mini model in the example below, but you can review different [LLM providers](https://github.com/ahuang11/MoreThanAChatBot/blob/main/docs/level1/providers.md) to choose a model most appropriate for your use:

```r
# Initialize the chat interface with the specified model
chat <- chat_openai(model = 'gpt-4o-mini')

# Extract data based on the defined structure
trends <- chat$extract_data(pdf_text, type = type_summary)

# Display the extracted data
print(trends)
```

The `chat$extract_data` function processes the extracted PDF text and retrieves data matching the defined structure. We can see from the data that there are multiple species experiencing declines. Let's say that we're interested in better understanding the threats faced by *Capensibufo rosei*.

## Extracting Text from the Remaining PDFs

Now we'll use the remaining PDFs to extract information about why the species is declining. First, we'll extract the text from these PDFs:

```r
# List files in folder
pdf_files <- list.files(path = "./pdf", pattern = "pdf$",
                        full.names = T)

# Extract text from last three
pdf_texts <- lapply(pdf_files[2:4], pdf_text)
```

## Defining the Data Structure for Threats

Now we'll define a new data structure that extracts information about threats.

```r
# Define the expected data structure
type_summary <- type_array("An array containing a row for every species for which a trend in population through time is mentioned",
                           items = type_object("Data on trends through time for a single species",
                                               title = type_string("Title of the paper"),
                                               year = type_integer("Year the paper was published"),
                                               threats = type_string("Brief description of cause for the decline of this species. Limit the description to five words. Create a new output for each cause. If there are multiple causes within a paper, repeat the paper's title on a new line with the additional cause.")
  )
)

```

## Extracting Threats Using the LLM

We'll repeat a similar process to above, but try a system prompt to initiate the model.

```r

# Initialize the chat interface with the specified model
chat <- chat_openai(model = 'gpt-4o-mini',
                    system_prompt = "You are a graduate student researcher who excels at reading and succinctly summarizing articles.")

# Extract data based on the defined structure
threats <- map_dfr(pdf_texts, ~ chat$extract_data(.x, type = type_summary))

# Display the extracted data
print(threats)
```

## Conclusion

By following this approach, you can efficiently extract structured ecological data from scientific PDFs using LLMs, thereby enhancing your research workflow.

**Note:** Ensure that your PDF file is accessible and that your API key is valid. This method leverages the capabilities of LLMs to automate data extraction, making the research process more efficient. 
