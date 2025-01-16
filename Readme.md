
Goal of this project:
This repository aims to develop a pipeline to analyze arguments in financial analyst reports. This involves the extraction of text from PDFs, the extraction of arguments and their sentiment as well as the analysis of arguments across industries and ratings as well as the difference between successful and unsuccessful reports.

Folder Structure of the project:
company_info.csv: contains the company name, the ticker symbol at the stock market and the industry and is important to be later linked to the report.

get_stock_prices.ipynb: creates performance_data.csv by using the yfinance library in python to retrieve the ‘Close’ prices for the selected timeframe (2014-2022).

performance_data.csv: contains the daily stock prices for the selected companies from 2014-2022

preprocessing.ipynb: responsible to the whole part of pre-processing the text. Utilizes pdfplumber to extract the textual information and regular expressions to filter textual parts and terms like target price and rating. Additionally, it checks the validity of sentences using the module spacy. It handles the updates of target prices for companies with a split and generally cleans the data. At the end it returns the preprocessed reports, paragraphs and sentences.

provider_info.csv: contains the provider’s name, name in the file path, ending/price target/recommendation pattern

reports.csv: contains the reports after extraction including the extracted paragraphs

updated_target_prices_ratings.csv: contains the results of the manually updated target prices and ratings. Is merged back to the reports in pre-processing steps.

gpt.ipynb: contains API connection to OpenAI and extracts the arguments from the preprocessed paragraphs and assigns sentiment. Returns dataframe that contains the arguments and sentiment for every report.

preprocessed_paragraphs.csv: contains the cleaned dataframe with paragraphs for every report

preprocessed_sentences.csv: contains the cleaned dataframe with all sentences for every paragraph and report
        
preprocessed_reports.csv: contains the cleaned dataframe with all reports and the related paragraphs as a list

evaluation_sentence.csv: contains a list of 150 sentences that are labelled with an argument and sentiment
        
gpt_evaluation.ipynb: extracts the arguments and sentiment for the test sentences using GPT models and calculates the evaluation metrics for the results

keybert_financialbert_evaluation.ipynb: extracts the arguments and sentiment for the test sentences using AdaptKeyBERT and FinancialBERT and calculates the evaluation metrics for the results

llama_evaluation.ipynb: extracts the arguments and sentiment for the test sentences using LLaMa models and calculates the evaluation metrics for the results

analyse_results.ipynb: responsible to merge similar arguments together and calculates the argument opinion score and accuracy for reports and arguments. Also, reviews the results for industry and ratings. For the statistical tests the library scipy.stats is used.

documents_analysis.ipynb: calculates the statistics for the documents regarding the pages (maximum, minimum, average, median)

argument_in_reports.csv: stores all arguments and related metrics regarding appearances

rating_argument_analysis.csv: stores argument numbers for ratings

reports_data.csv: contains report information especially for target prices

statistical_significance.csv: contains the results of the statistical test