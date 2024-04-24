# AWS Example of PDF file to Summarization using AWS Machine Learning Technology

The goal is to take a PDF file, such as one created from an Amazon research call, and create a summarization, with sentiment, of dialogue using AWS services.

Like many existing services, the Python notebook will take a small PDF file and create a  summarization using a Large Language Model. The application utilizes the following AWS services:

- Bedrock - Provides the LLM (Titan) to create the summarization of the dialogue
- Cloudwatch - To record events generated from the code running in Lambda

By creating this project, it provides more control over what is generated in the summarization and data privacy verses using a third party. There are two notebooks:

- PDF_summarizer_non_lambda will run the python code locally and  use the AWS Bedrock LLM to do the summarization.

- PDF_summarizer.with.lambda is designed to used AWS Lambda function and S3 to execute the code and will use the Bedrock LLM to perform the summarization. Due to the function with its dependency layers exceeding the AWS 250 MB limit, it will need to be ported to a container.

## Pre-configured Requirements
- IAM policies for Bedrock and Cloudwatch

The PDF_summarizer_non_lambda project is divided into two parts:

## Part 1: Load the PDF file and split the PDF into text chunks
The notebook will load the PDF from the local file system and create docs from a text splitter. These chunks or docs are passed into the summarization chain.

## Part 2: Map reduce summarization chain
The document text chunks are inputted into a LangChain map reduce summarizer. Each document chunk is summarized in the map step and then the summaries are reduced to a final summary. There are two prompts, one for the individual document summary and one for the final summary.

### Next Steps
Port the code to execute in a AWS Lambda container



### References
DeepLearning.ai's Serverless LLM apps with Amazon Bedrock with Mike Chambers.
